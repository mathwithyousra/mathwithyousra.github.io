/*
Math With Yousra — {5,4} Poincaré disk logo

This source constructs the tessellation mathematically.
It does not embed or rasterize the reference image.
*/

(() => {
  const svg = document.getElementById("poincare-logo");
  if (!svg) return;

  const NS = "http://www.w3.org/2000/svg";
  const P = 5, Q = 4;
  const SIZE = 1000, CENTER = 500, DISK_R = 494;
  const MAX_DEPTH = 9;
  const ROT = 45.4 * Math.PI / 180;

  const C = (re, im = 0) => ({ re, im });
  const add = (a, b) => C(a.re + b.re, a.im + b.im);
  const sub = (a, b) => C(a.re - b.re, a.im - b.im);
  const mul = (a, b) =>
    C(
      a.re * b.re - a.im * b.im,
      a.re * b.im + a.im * b.re
    );

  const conj = a => C(a.re, -a.im);
  const scale = (a, s) => C(a.re * s, a.im * s);
  const abs2 = a => a.re * a.re + a.im * a.im;
  const abs = a => Math.sqrt(abs2(a));
  const phase = a => Math.atan2(a.im, a.re);
  const expi = t => C(Math.cos(t), Math.sin(t));
  const acosh = x => Math.log(x + Math.sqrt(x * x - 1));

  /*
    Regular {5,4} central pentagon.

    For a regular {p,q} hyperbolic tessellation:

    cosh(R) = cot(pi/p) cot(pi/q)
  */
  const Rh = acosh(
    (1 / Math.tan(Math.PI / P)) *
    (1 / Math.tan(Math.PI / Q))
  );

  /*
    Convert hyperbolic circumradius R into
    Euclidean radius in the Poincaré disk.
  */
  const rho = Math.tanh(Rh / 2);

  function regularPolygon() {
    return Array.from({ length: P }, (_, k) =>
      scale(
        expi(ROT + 2 * Math.PI * k / P),
        rho
      )
    );
  }

  /*
    Find the Euclidean circle representing the
    Poincaré geodesic through z1 and z2.

    The circle is orthogonal to the unit disk boundary.
  */
  function geodesicCircle(z1, z2) {
    const x1 = z1.re;
    const y1 = z1.im;
    const x2 = z2.re;
    const y2 = z2.im;

    const b1 = (abs2(z1) + 1) / 2;
    const b2 = (abs2(z2) + 1) / 2;

    const det = x1 * y2 - y1 * x2;

    if (Math.abs(det) < 1e-13) {
      return null;
    }

    const cx = (b1 * y2 - y1 * b2) / det;
    const cy = (x1 * b2 - b1 * x2) / det;

    const c = C(cx, cy);

    return {
      c,
      r: Math.sqrt(Math.max(abs2(c) - 1, 0))
    };
  }

  /*
    Hyperbolic reflection across a Poincaré geodesic.
  */
  function reflect(z, a, b) {
    const g = geodesicCircle(a, b);

    if (!g) {
      return mul(
        expi(2 * phase(a)),
        conj(z)
      );
    }

    const w = sub(z, g.c);

    return add(
      g.c,
      scale(
        w,
        (g.r * g.r) / abs2(w)
      )
    );
  }

  function polygonKey(poly, d = 9) {
    return poly
      .map(z => [
        z.re.toFixed(d),
        z.im.toFixed(d)
      ])
      .sort(
        (u, v) =>
          Number(u[0]) - Number(v[0]) ||
          Number(u[1]) - Number(v[1])
      )
      .map(x => x.join(","))
      .join("|");
  }

  /*
    Generate the entire tessellation by repeatedly
    reflecting pentagons across their geodesic edges.
  */
  let tiles = [];
  let seen = new Set();
  let frontier = [regularPolygon()];

  for (
    let depth = 0;
    depth <= MAX_DEPTH;
    depth++
  ) {
    const next = [];

    for (const poly of frontier) {
      const key = polygonKey(poly);

      if (seen.has(key)) continue;

      seen.add(key);
      tiles.push(poly);

      for (let i = 0; i < P; i++) {
        const a = poly[i];
        const b = poly[(i + 1) % P];

        const child = poly.map(z =>
          reflect(z, a, b)
        );

        if (!seen.has(polygonKey(child))) {
          next.push(child);
        }
      }
    }

    frontier = next;
  }

  function edgeKey(a, b, d = 8) {
    const A =
      `${a.re.toFixed(d)},${a.im.toFixed(d)}`;

    const B =
      `${b.re.toFixed(d)},${b.im.toFixed(d)}`;

    return A < B
      ? `${A}|${B}`
      : `${B}|${A}`;
  }

  /*
    Remove duplicate edges.
  */
  const edges = new Map();

  for (const poly of tiles) {
    for (let i = 0; i < P; i++) {
      const a = poly[i];
      const b = poly[(i + 1) % P];

      const k = edgeKey(a, b);

      if (!edges.has(k)) {
        edges.set(k, [a, b]);
      }
    }
  }

  /*
    Sample points along each Poincaré geodesic.
  */
  function sampleGeodesic(a, b, n = 22) {
    const g = geodesicCircle(a, b);

    if (!g) {
      return Array.from(
        { length: n + 1 },
        (_, k) =>
          add(
            a,
            scale(
              sub(b, a),
              k / n
            )
          )
      );
    }

    const t1 = phase(
      sub(a, g.c)
    );

    const t2 = phase(
      sub(b, g.c)
    );

    let raw =
      (
        (
          t2 - t1 + Math.PI
        ) %
        (2 * Math.PI) +
        2 * Math.PI
      ) %
      (2 * Math.PI) -
      Math.PI;

    const alt =
      raw > 0
        ? raw - 2 * Math.PI
        : raw + 2 * Math.PI;

    let delta = raw;

    for (const d of [raw, alt]) {
      const mid = add(
        g.c,
        scale(
          expi(t1 + d / 2),
          g.r
        )
      );

      if (abs(mid) < 1 + 1e-8) {
        delta = d;
        break;
      }
    }

    return Array.from(
      { length: n + 1 },
      (_, k) =>
        add(
          g.c,
          scale(
            expi(
              t1 +
              delta * k / n
            ),
            g.r
          )
        )
    );
  }

  /*
    Convert unit-disk coordinates to SVG coordinates.
  */
  const xy = z => [
    CENTER + DISK_R * z.re,
    CENTER - DISK_R * z.im
  ];

  /*
    White background.
  */
  const bg =
    document.createElementNS(
      NS,
      "rect"
    );

  bg.setAttribute(
    "width",
    SIZE
  );

  bg.setAttribute(
    "height",
    SIZE
  );

  bg.setAttribute(
    "fill",
    "#fff"
  );

  svg.appendChild(bg);

  /*
    Clip tessellation to circular disk.
  */
  const defs =
    document.createElementNS(
      NS,
      "defs"
    );

  const clip =
    document.createElementNS(
      NS,
      "clipPath"
    );

  clip.id = "diskClip";

  const clipCircle =
    document.createElementNS(
      NS,
      "circle"
    );

  clipCircle.setAttribute(
    "cx",
    CENTER
  );

  clipCircle.setAttribute(
    "cy",
    CENTER
  );

  clipCircle.setAttribute(
    "r",
    DISK_R
  );

  clip.appendChild(
    clipCircle
  );

  defs.appendChild(
    clip
  );

  svg.appendChild(
    defs
  );

  /*
    Draw geodesics.
  */
  const group =
    document.createElementNS(
      NS,
      "g"
    );

  group.setAttribute(
    "clip-path",
    "url(#diskClip)"
  );

  group.setAttribute(
    "fill",
    "none"
  );

  group.setAttribute(
    "stroke",
    "#000"
  );

  group.setAttribute(
    "stroke-linecap",
    "round"
  );

  group.setAttribute(
    "stroke-linejoin",
    "round"
  );

  for (
    const [a, b]
    of edges.values()
  ) {
    const pts =
      sampleGeodesic(a, b);

    const rmin =
      Math.min(
        ...pts.map(abs)
      );

    if (rmin >= 0.99965) {
      continue;
    }

    /*
      Thick central geodesics,
      progressively finer toward
      the ideal boundary.
    */
    const stroke =
      20 *
      Math.max(
        0.055,
        1 - rmin * rmin
      );

    const coords =
      pts.map(xy);

    const path =
      document.createElementNS(
        NS,
        "path"
      );

    path.setAttribute(
      "d",
      "M " +
      coords
        .map(
          ([x, y]) =>
            `${x.toFixed(3)},${y.toFixed(3)}`
        )
        .join(" L ")
    );

    path.setAttribute(
      "stroke-width",
      stroke.toFixed(3)
    );

    group.appendChild(
      path
    );
  }

  svg.appendChild(
    group
  );

  /*
    Ideal boundary of the Poincaré disk.
  */
  const boundary =
    document.createElementNS(
      NS,
      "circle"
    );

  boundary.setAttribute(
    "cx",
    CENTER
  );

  boundary.setAttribute(
    "cy",
    CENTER
  );

  boundary.setAttribute(
    "r",
    DISK_R
  );

  boundary.setAttribute(
    "fill",
    "none"
  );

  boundary.setAttribute(
    "stroke",
    "#000"
  );

  boundary.setAttribute(
    "stroke-width",
    "1.8"
  );

  svg.appendChild(
    boundary
  );
})();
