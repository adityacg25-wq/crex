# CREX Consulting Group

A responsive multipage Next.js website for CREX's real estate advisory, leasing, project marketing, finance and taxation, and commercial interiors services.

## Run locally

Requires Node.js 24 and pnpm 11.

```sh
pnpm install
pnpm dev
```

Open `http://127.0.0.1:3000`. For production, run `pnpm build` followed by `pnpm start`.

## Checks

```sh
pnpm lint
pnpm typecheck
pnpm test
pnpm test:e2e
```

Browser regression tests expect the app to be running. Install the test browser with `pnpm exec playwright install chromium` once, or use `PLAYWRIGHT_CHROME_EXECUTABLE` to select an installed Chrome executable. Test submissions use intercepted responses and never email CREX.

## Enquiry delivery

Copy `.env.example` to `.env.local` and configure:

| Variable | Purpose |
| --- | --- |
| `NEXT_PUBLIC_SITE_URL` | Public canonical deployment URL. Defaults to `https://crex.co.in`. |
| `RESEND_API_KEY` | Server-only Resend API key. |
| `RESEND_FROM_EMAIL` | Sender on a domain verified in Resend, e.g. `CREX Website <website@crex.co.in>`. |
| `CREX_ENQUIRY_EMAIL` | Recipient. Defaults to `sales@crex.co.in`. |

The server validates enquiries, bounds request size, checks browser origins and applies a small process-local rate limit. It sends plain-text email with the visitor's email as the reply-to address. Success appears only when the provider accepts delivery. Without mail configuration, the form shows a helpful failure and direct WhatsApp contact; it does not simulate sending. Telephone, email, WhatsApp and directions links are usable independently.

For a multi-instance production deployment, replace the process-local rate limiter with a trusted shared store and configure proxy headers at the hosting edge. The website has no database, customer login, analytics or advertising cookies. Review the privacy page against the final deployment and company retention practices before launch.

## Content and assets

Edit `src/content/site.ts` for company details, the five services, four consulting partners, six testimonial excerpts and three articles. Existing service and company page slugs are retained. The blog contains newly written practical articles based on the supplied brief and CREX's services; demo WordPress posts were excluded.

The supplied logo, address and phone number take precedence over the old website. Service descriptions, partner biographies, testimonial excerpts, sales email and social links were sourced from CREX's published website. See `outputs/build-notes.md` for provenance and image prompts. Validate company information before public launch.

The three architectural images are AI-generated representative imagery, never presented as completed CREX projects. Client logos came from the existing CREX testimonials. Manrope and Syncopate are self-hosted with their licenses alongside the fonts; interface icons come from Phosphor. The design uses one green accent, consistent corners, semantic colour tokens, a permanent green-and-white light appearance and reduced-motion support.

## Deployment

Deploy to a Next.js-compatible Node host, configure the environment variables above, and run the production build. Static company and service pages are prerendered; contact enquiries use a Node route handler. Metadata, an Open Graph image, `robots.txt`, `sitemap.xml` and basic security headers are included. No public deployment is performed by this repository setup.
