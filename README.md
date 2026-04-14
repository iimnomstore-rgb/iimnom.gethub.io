# iimnom.gethub.io
IIMNOM stands for “It’s In Me Not On Me,” a bold statement of confidence, authenticity, and style that comes from within. We blend urban culture, luxury design, and everyday lifestyle products to create a shopping experience that feels modern, classy, and unforgettable.
import React, { useMemo, useState } from "react";
import { motion } from "framer-motion";
import {
  Search,
  Upload,
  Star,
  ArrowRight,
  ShoppingBag,
  Heart,
  FolderOpen,
  Image as ImageIcon,
  Download,
  Mail,
  Crown,
  Sparkles,
  TrendingUp,
  Package,
  PawPrint,
  Home,
  Bed,
  Bath,
  Store,
  CreditCard,
  ShieldCheck,
  CheckCircle2,
  Bell,
  BarChart3,
  Menu,
  Megaphone,
} from "lucide-react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Badge } from "@/components/ui/badge";
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";

const logoImage = "/mnt/data/Screenshot 2026-03-28 093212.png";
const moodBoardImage = "/mnt/data/a_series_of_website_mockups_exhibit_a_trendy_urban.png";

const featuredProducts = [
  {
    id: 1,
    title: "Rocko Pet Hoodie",
    price: "$48.99",
    sale: "$44.34",
    category: "Pet Wear",
    image: moodBoardImage,
  },
  {
    id: 2,
    title: "Queens Only Tumbler",
    price: "$32.99",
    sale: "$29.99",
    category: "Drinkware",
    image: moodBoardImage,
  },
  {
    id: 3,
    title: "We All We Got Tee",
    price: "$34.99",
    sale: "$29.99",
    category: "Streetwear",
    image: moodBoardImage,
  },
  {
    id: 4,
    title: "Street Legend Wall Art",
    price: "$34.99",
    sale: "$31.99",
    category: "Home Decor",
    image: moodBoardImage,
  },
];

const etsyReadyProducts = [
  {
    title: "IIMNOM ‘Queens Only’ Skinny Tumbler",
    price: "$29.99",
    badge: "Etsy Ready",
    description:
      "Bold black-and-gold tumbler featuring the official IIMNOM logo and upscale urban styling. Great for iced coffee, gifting, boss energy, and daily use.",
    bullets: [
      "20 oz skinny tumbler",
      "Gloss finish with wraparound design",
      "Urban luxe gift idea",
      "Perfect for women who love bold statement style",
    ],
  },
  {
    title: "IIMNOM ‘Real Don’t Rub Off’ Unisex Tee",
    price: "$29.95",
    badge: "Best Seller",
    description:
      "Classic black statement shirt with the official IIMNOM logo and signature slogan. Stylish enough for streetwear, casual layering, or brand photography.",
    bullets: [
      "Unisex fit",
      "Soft everyday fabric feel",
      "Black, gold, and white brand styling",
      "Perfect for streetwear lovers",
    ],
  },
  {
    title: "IIMNOM Pet Bandana Mockup Design",
    price: "$18.95",
    badge: "Pet Line",
    description:
      "A clean, stylish pet accessory design for customers who want their pets included in the brand lifestyle. Great add-on product for dog lovers.",
    bullets: [
      "Easy giftable item",
      "Pairs well with owner matching apparel",
      "Urban pet collection look",
      "Great upsell on Etsy and Shopify",
    ],
  },
  {
    title: "IIMNOM Bedroom Decor ZIP Bundle",
    price: "$12.99",
    badge: "Digital Download",
    description:
      "A digital home decor concept bundle featuring luxe bedroom branding visuals inspired by the IIMNOM style. Great for printable decor bundles and instant download sales.",
    bullets: [
      "Instant digital product",
      "Designed for decor lovers",
      "Strong black-gold-pink urban aesthetic",
      "Perfect for home styling collections",
    ],
  },
  {
    title: "IIMNOM Business Branding Starter Pack",
    price: "$16.99",
    badge: "Brand Kit",
    description:
      "Includes matching visual concepts for tumbler, tee, business card, and social-style product branding. Great for a signature launch listing or promo bundle.",
    bullets: [
      "Brand-forward product presentation",
      "High perceived value",
      "Great for launch promos",
      "Ideal for Etsy, Shopify, and custom orders",
    ],
  },
];

function GlowButton({ children, className = "", ...props }) {
  return (
    <Button
      {...props}
      className={`rounded-full border border-yellow-300/50 bg-gradient-to-r from-yellow-200 via-yellow-400 to-yellow-600 px-6 py-6 text-sm font-semibold uppercase tracking-[0.18em] text-black shadow-[0_0_30px_rgba(255,200,80,0.35)] transition hover:scale-[1.02] hover:shadow-[0_0_50px_rgba(255,200,80,0.5)] ${className}`}
    >
      {children}
    </Button>
  );
}

function ProductCard({ product }) {
  return (
    <motion.div whileHover={{ y: -6 }} transition={{ duration: 0.25 }}>
      <Card className="overflow-hidden rounded-[28px] border border-yellow-400/20 bg-[#0e0a0f] shadow-[0_0_0_1px_rgba(255,200,80,0.06),0_20px_60px_rgba(0,0,0,0.45)]">
        <div className="relative aspect-[4/4.7] overflow-hidden">
          <img src={product.image} alt={product.title} className="h-full w-full object-cover opacity-90" />
          <div className="absolute inset-0 bg-gradient-to-t from-black via-black/25 to-transparent" />
          <div className="absolute left-4 top-4">
            <Badge className="rounded-full border border-yellow-300/30 bg-black/70 text-yellow-200 hover:bg-black/70">
              {product.category}
            </Badge>
          </div>
        </div>
        <CardContent className="space-y-3 p-5 text-white">
          <h3 className="text-xl font-semibold tracking-tight">{product.title}</h3>
          <div className="flex items-center gap-1 text-yellow-300">
            {Array.from({ length: 5 }).map((_, i) => (
              <Star key={i} className="h-4 w-4 fill-current" />
            ))}
          </div>
          <div className="flex items-center justify-between">
            <div className="flex items-center gap-2">
              <span className="rounded-full border border-yellow-300/20 bg-yellow-300/10 px-3 py-1 text-xs uppercase tracking-[0.18em] text-yellow-100">
                Sale
              </span>
              <span className="text-lg font-bold text-yellow-300">{product.sale}</span>
            </div>
            <span className="text-sm text-white/55 line-through">{product.price}</span>
          </div>
        </CardContent>
      </Card>
    </motion.div>
  );
}

function EtsyProductBlock({ item }) {
  return (
    <Card className="rounded-[28px] border border-yellow-300/15 bg-white text-black shadow-lg">
      <CardContent className="p-6">
        <div className="mb-3 flex items-start justify-between gap-3">
          <div>
            <p className="text-xs font-semibold uppercase tracking-[0.2em] text-black/50">{item.badge}</p>
            <h3 className="mt-2 text-xl font-semibold leading-tight">{item.title}</h3>
          </div>
          <Badge className="rounded-full bg-black text-white hover:bg-black">{item.price}</Badge>
        </div>
        <p className="text-sm leading-6 text-black/70">{item.description}</p>
        <ul className="mt-4 space-y-2 text-sm text-black/75">
          {item.bullets.map((bullet) => (
            <li key={bullet} className="flex items-start gap-2">
              <CheckCircle2 className="mt-0.5 h-4 w-4 text-green-600" />
              <span>{bullet}</span>
            </li>
          ))}
        </ul>
      </CardContent>
    </Card>
  );
}

function SectionHeader({ eyebrow, title, body }) {
  return (
    <div className="max-w-3xl">
      <p className="mb-3 text-xs font-semibold uppercase tracking-[0.28em] text-yellow-300/80">{eyebrow}</p>
      <h2 className="text-3xl font-semibold tracking-tight text-white md:text-5xl">{title}</h2>
      <p className="mt-4 text-base leading-7 text-white/70 md:text-lg">{body}</p>
    </div>
  );
}

export default function IIMNOMUrbanLuxurySite() {
  const [search, setSearch] = useState("");
  const [activeRoom, setActiveRoom] = useState("Bedroom");
  const [email, setEmail] = useState("");

  const filteredProducts = useMemo(() => {
    if (!search.trim()) return featuredProducts;
    return featuredProducts.filter((item) =>
      `${item.title} ${item.category}`.toLowerCase().includes(search.toLowerCase())
    );
  }, [search]);

  return (
    <div className="min-h-screen bg-[#050205] text-white">
      <div className="fixed inset-0 -z-10 bg-[radial-gradient(circle_at_20%_10%,rgba(255,0,180,0.18),transparent_20%),radial-gradient(circle_at_85%_15%,rgba(255,210,70,0.18),transparent_22%),radial-gradient(circle_at_50%_80%,rgba(255,140,0,0.12),transparent_28%),linear-gradient(180deg,#070308_0%,#12070d_30%,#090508_100%)]" />

      <header className="sticky top-0 z-40 border-b border-white/10 bg-black/55 backdrop-blur-xl">
        <div className="mx-auto flex max-w-7xl items-center justify-between px-6 py-4 md:px-10">
          <div className="flex items-center gap-3">
            <img src={logoImage} alt="IIMNOM official logo" className="h-12 w-12 rounded-full object-cover shadow-[0_0_25px_rgba(255,80,180,0.45)]" />
            <div>
              <p className="text-lg font-semibold tracking-[0.12em] text-white">IIMNOM</p>
              <p className="text-xs uppercase tracking-[0.22em] text-pink-300">It’s In Me Not On Me</p>
            </div>
          </div>

          <nav className="hidden items-center gap-6 text-sm uppercase tracking-[0.18em] text-white/75 lg:flex">
            <a href="#shop" className="hover:text-yellow-300">Shop</a>
            <a href="#customize" className="hover:text-yellow-300">Customize</a>
            <a href="#admin" className="hover:text-yellow-300">Admin</a>
            <a href="#etsy" className="hover:text-yellow-300">Etsy Ready</a>
            <a href="#contact" className="hover:text-yellow-300">Contact</a>
          </nav>

          <div className="flex items-center gap-3">
            <Button variant="ghost" className="hidden rounded-full text-white hover:bg-white/10 md:inline-flex">
              <Heart className="mr-2 h-4 w-4" /> Wishlist
            </Button>
            <GlowButton className="hidden md:inline-flex">
              <ShoppingBag className="mr-2 h-4 w-4" /> Shop Now
            </GlowButton>
            <Button variant="ghost" className="rounded-full text-white hover:bg-white/10 lg:hidden">
              <Menu className="h-5 w-5" />
            </Button>
          </div>
        </div>
      </header>

      <main>
        <section className="relative overflow-hidden border-b border-yellow-400/10">
          <div className="mx-auto grid max-w-7xl gap-10 px-6 py-14 md:px-10 lg:grid-cols-[1.05fr_0.95fr] lg:py-20">
            <div className="flex flex-col justify-center">
              <Badge className="w-fit rounded-full border border-pink-300/25 bg-pink-300/10 px-4 py-2 text-xs uppercase tracking-[0.28em] text-pink-200 hover:bg-pink-300/10">
                Official IIMNOM Brand Site
              </Badge>
              <h1 className="mt-6 max-w-4xl text-4xl font-semibold leading-[0.95] tracking-tight text-white md:text-6xl lg:text-7xl">
                Dress fresh. Live bold. Stay true.
              </h1>
              <p className="mt-5 max-w-2xl text-lg leading-8 text-white/72">
                A stylish street-luxury POD store built around your official IIMNOM logo, powerful slogan,
                mockup-based shopping, bold product drops, and high-converting visuals designed to turn attention into sales.
              </p>
              <div className="mt-8 flex flex-wrap gap-4">
                <GlowButton>
                  Shop New Arrivals <ArrowRight className="ml-2 h-4 w-4" />
                </GlowButton>
                <Button variant="outline" className="rounded-full border-white/15 bg-white/5 px-6 py-6 text-sm uppercase tracking-[0.18em] text-white hover:bg-white/10">
                  Build Your Custom Look
                </Button>
              </div>
              <div className="mt-8 flex flex-wrap gap-3 text-xs uppercase tracking-[0.2em] text-white/65">
                <span className="rounded-full border border-white/10 bg-white/5 px-4 py-2">Urban</span>
                <span className="rounded-full border border-white/10 bg-white/5 px-4 py-2">Luxury</span>
                <span className="rounded-full border border-white/10 bg-white/5 px-4 py-2">Classy</span>
                <span className="rounded-full border border-white/10 bg-white/5 px-4 py-2">POD Ready</span>
              </div>
            </div>

            <motion.div
              initial={{ opacity: 0, y: 30 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.7 }}
              className="relative"
            >
              <div className="absolute -inset-6 rounded-[40px] bg-gradient-to-r from-pink-500/20 via-yellow-400/15 to-orange-500/20 blur-3xl" />
              <div className="relative overflow-hidden rounded-[34px] border border-yellow-400/20 bg-black/45 shadow-[0_30px_80px_rgba(0,0,0,0.55)]">
                <img src={moodBoardImage} alt="IIMNOM homepage mood board" className="h-full w-full object-cover" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/55 to-transparent" />
              </div>
            </motion.div>
          </div>
        </section>

        <section className="border-b border-white/10 bg-black/25 py-5">
          <div className="mx-auto flex max-w-7xl flex-wrap items-center justify-center gap-4 px-6 text-center text-sm uppercase tracking-[0.3em] text-yellow-200/80 md:px-10">
            <span>Stay Ahead of the Trends</span>
            <span className="hidden md:inline">•</span>
            <span>Shop Our Latest Drops</span>
            <span className="hidden md:inline">•</span>
            <span>Turn Heads & Make Moves</span>
          </div>
        </section>

        <section id="shop" className="mx-auto max-w-7xl px-6 py-16 md:px-10">
          <div className="mb-8 flex flex-col gap-5 lg:flex-row lg:items-end lg:justify-between">
            <SectionHeader
              eyebrow="New Drops"
              title="Show-stopping storefront made to feel rich, bold, and unforgettable."
              body="This layout is styled to match the uploaded image direction with glowing gold buttons, dark luxury panels, strong product cards, and urban glamour energy."
            />
            <div className="w-full max-w-md">
              <div className="relative">
                <Search className="pointer-events-none absolute left-4 top-1/2 h-4 w-4 -translate-y-1/2 text-black/40" />
                <Input
                  value={search}
                  onChange={(e) => setSearch(e.target.value)}
                  placeholder="Search shirts, tumblers, pet wear, decor"
                  className="rounded-full border-yellow-300/20 bg-white pl-11 text-black placeholder:text-black/45"
                />
              </div>
            </div>
          </div>

          <div className="grid gap-6 lg:grid-cols-[0.95fr_1.05fr]">
            <Card className="overflow-hidden rounded-[34px] border border-yellow-400/15 bg-[#100910] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
              <CardContent className="grid gap-6 p-6 lg:grid-cols-[0.75fr_1fr] lg:p-8">
                <div className="rounded-[28px] border border-yellow-400/15 bg-black/35 p-4">
                  <div className="overflow-hidden rounded-[22px]">
                    <img src={moodBoardImage} alt="IIMNOM hoodie preview" className="h-full w-full object-cover" />
                  </div>
                </div>

                <div>
                  <h3 className="text-3xl font-semibold tracking-tight text-yellow-100 md:text-4xl">Upload Files</h3>
                  <p className="mt-3 max-w-xl text-base leading-7 text-white/70">
                    Bring in product art, mockups, and bundles from your computer, Google Drive, Google Photos,
                    or your supplier feeds. Keep your library fresh and easy to manage from one clean admin space.
                  </p>
                  <div className="mt-6 grid gap-3">
                    {[
                      { icon: FolderOpen, label: "Browse Files" },
                      { icon: Upload, label: "Bulk Upload ZIPs" },
                      { icon: ImageIcon, label: "Google Drive Import" },
                      { icon: Download, label: "Google Photos Import" },
                    ].map(({ icon: Icon, label }) => (
                      <div key={label} className="flex items-center justify-between rounded-2xl border border-yellow-400/15 bg-black/30 px-4 py-4">
                        <div className="flex items-center gap-3">
                          <div className="rounded-xl bg-yellow-300/10 p-2 text-yellow-300">
                            <Icon className="h-4 w-4" />
                          </div>
                          <span className="text-sm uppercase tracking-[0.18em] text-white/85">{label}</span>
                        </div>
                        <ArrowRight className="h-4 w-4 text-yellow-300" />
                      </div>
                    ))}
                  </div>
                </div>
              </CardContent>
            </Card>

            <Card className="overflow-hidden rounded-[34px] border border-yellow-400/15 bg-[#100910] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
              <CardContent className="p-6 lg:p-8">
                <div className="overflow-hidden rounded-[28px] border border-yellow-400/15 bg-black/30">
                  <img src={moodBoardImage} alt="room mockup preview" className="h-full w-full object-cover" />
                </div>
                <div className="mt-5 flex flex-wrap items-center justify-between gap-4">
                  <div>
                    <p className="text-xs uppercase tracking-[0.25em] text-yellow-200/70">Home Decor Mockup</p>
                    <h3 className="mt-2 text-2xl font-semibold text-white">Start customizing</h3>
                  </div>
                  <GlowButton>Customize Now</GlowButton>
                </div>
              </CardContent>
            </Card>
          </div>

          <div className="mt-10 grid gap-6 sm:grid-cols-2 xl:grid-cols-4">
            {filteredProducts.map((product) => (
              <ProductCard key={product.id} product={product} />
            ))}
          </div>
        </section>

        <section id="customize" className="border-y border-white/10 bg-black/25">
          <div className="mx-auto max-w-7xl px-6 py-16 md:px-10">
            <SectionHeader
              eyebrow="Create and Personalize"
              title="Pet avatars, room mockups, and statement products built for your niche."
              body="Use reusable mockup images, customer-facing personalization previews, and supplier-connected products for fast launches and stronger conversion."
            />

            <div className="mt-10 grid gap-6 lg:grid-cols-[0.95fr_1.05fr]">
              <Card className="rounded-[32px] border border-yellow-300/15 bg-white text-black shadow-lg">
                <CardContent className="p-6 md:p-8">
                  <Tabs defaultValue="pet">
                    <TabsList className="grid w-full grid-cols-3 rounded-2xl bg-black/5 p-1">
                      <TabsTrigger value="pet" className="rounded-xl data-[state=active]:bg-black data-[state=active]:text-white">Pet Avatar</TabsTrigger>
                      <TabsTrigger value="room" className="rounded-xl data-[state=active]:bg-black data-[state=active]:text-white">Room Mockup</TabsTrigger>
                      <TabsTrigger value="fashion" className="rounded-xl data-[state=active]:bg-black data-[state=active]:text-white">Fashion Builder</TabsTrigger>
                    </TabsList>

                    <TabsContent value="pet" className="mt-6 space-y-4">
                      <div className="grid gap-4 md:grid-cols-2">
                        <div className="rounded-[24px] bg-neutral-100 p-4">
                          <p className="mb-3 flex items-center gap-2 font-semibold"><PawPrint className="h-4 w-4" /> Pet builder</p>
                          <Input placeholder="Breed or pet type" className="rounded-2xl bg-white" />
                          <Input placeholder="Color / markings / size" className="mt-3 rounded-2xl bg-white" />
                          <Input placeholder="Style notes for pet outfit" className="mt-3 rounded-2xl bg-white" />
                        </div>
                        <div className="overflow-hidden rounded-[24px] bg-black">
                          <img src={moodBoardImage} alt="pet avatar mockup" className="h-full w-full object-cover" />
                        </div>
                      </div>
                    </TabsContent>

                    <TabsContent value="room" className="mt-6 space-y-4">
                      <div className="flex flex-wrap gap-3">
                        {[
                          { name: "Bedroom", icon: Bed },
                          { name: "Living Room", icon: Home },
                          { name: "Bathroom", icon: Bath },
                        ].map(({ name, icon: Icon }) => (
                          <Button
                            key={name}
                            onClick={() => setActiveRoom(name)}
                            className={`rounded-full ${activeRoom === name ? "bg-black text-white hover:bg-black" : "bg-neutral-100 text-black hover:bg-neutral-200"}`}
                          >
                            <Icon className="mr-2 h-4 w-4" /> {name}
                          </Button>
                        ))}
                      </div>
                      <div className="overflow-hidden rounded-[28px] bg-black">
                        <img src={moodBoardImage} alt={`${activeRoom} mockup`} className="h-full w-full object-cover" />
                      </div>
                    </TabsContent>

                    <TabsContent value="fashion" className="mt-6">
                      <div className="grid gap-4 md:grid-cols-2">
                        <div className="space-y-3 rounded-[24px] bg-neutral-100 p-4">
                          <Input placeholder="Apparel type" className="rounded-2xl bg-white" />
                          <Input placeholder="Urban / classy / sexy / clean notes" className="rounded-2xl bg-white" />
                          <Input placeholder="Customer personalization text" className="rounded-2xl bg-white" />
                          <GlowButton className="w-full">Preview Design</GlowButton>
                        </div>
                        <div className="overflow-hidden rounded-[24px] bg-black">
                          <img src={moodBoardImage} alt="fashion product preview" className="h-full w-full object-cover" />
                        </div>
                      </div>
                    </TabsContent>
                  </Tabs>
                </CardContent>
              </Card>

              <div className="grid gap-6">
                <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
                  <CardContent className="p-6 text-white">
                    <p className="text-xs uppercase tracking-[0.25em] text-pink-300/80">Official Brand Products</p>
                    <h3 className="mt-3 text-2xl font-semibold">Business product pack</h3>
                    <div className="mt-5 grid gap-3 text-sm text-white/78">
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Logo tee design</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Tumbler product artwork</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Owner business cards</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Letterhead concept</div>
                    </div>
                  </CardContent>
                </Card>

                <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
                  <CardContent className="p-6 text-white">
                    <p className="text-xs uppercase tracking-[0.25em] text-yellow-200/70">Revenue Features</p>
                    <div className="mt-4 grid gap-3 text-sm text-white/78">
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Bundle discounts and upsells</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Email coupon signup popups</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Holiday drop reminders</div>
                      <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Top-seller and trending sections</div>
                    </div>
                  </CardContent>
                </Card>
              </div>
            </div>
          </div>
        </section>

        <section id="admin" className="mx-auto max-w-7xl px-6 py-16 md:px-10">
          <div className="grid gap-6 lg:grid-cols-[1.1fr_0.9fr]">
            <div className="space-y-6">
              <SectionHeader
                eyebrow="Admin Hub"
                title="One place to run uploads, bundles, campaigns, and sales growth."
                body="This admin section is designed for bulk image uploads, ZIP product management, subscriber growth, trend planning, and profit tracking."
              />
              <div className="grid gap-5 md:grid-cols-2">
                {[
                  { icon: Upload, title: "Bulk Image Uploads", body: "Import from desktop, Drive, Photos, and supplier feeds." },
                  { icon: Package, title: "ZIP Bundle Builder", body: "Create single ZIP files or grouped digital product bundles." },
                  { icon: Mail, title: "Coupon Campaigns", body: "Send offers, sales alerts, launch emails, and subscriber promos." },
                  { icon: TrendingUp, title: "Trend Suggestions", body: "Track what to post next for holidays, seasons, and fast-selling items." },
                ].map(({ icon: Icon, title, body }) => (
                  <Card key={title} className="rounded-[28px] border border-yellow-400/15 bg-white text-black shadow-lg">
                    <CardContent className="p-6">
                      <div className="mb-4 inline-flex rounded-2xl bg-yellow-100 p-3 text-black">
                        <Icon className="h-5 w-5" />
                      </div>
                      <h3 className="text-xl font-semibold">{title}</h3>
                      <p className="mt-3 text-sm leading-6 text-black/70">{body}</p>
                    </CardContent>
                  </Card>
                ))}
              </div>
            </div>

            <div className="grid gap-6">
              <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
                <CardContent className="p-6 text-white">
                  <div className="flex items-start justify-between gap-3">
                    <div>
                      <p className="text-xs uppercase tracking-[0.25em] text-yellow-200/70">Sales Snapshot</p>
                      <h3 className="mt-2 text-2xl font-semibold">Profit dashboard</h3>
                    </div>
                    <BarChart3 className="h-5 w-5 text-yellow-300" />
                  </div>
                  <div className="mt-5 grid gap-3">
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Daily Sales: <span className="font-semibold text-yellow-300">$438</span></div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Weekly Sales: <span className="font-semibold text-yellow-300">$3,920</span></div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Monthly Sales: <span className="font-semibold text-yellow-300">$17,600</span></div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Top Category: <span className="font-semibold text-yellow-300">Tumblers + Tee Bundles</span></div>
                  </div>
                </CardContent>
              </Card>

              <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
                <CardContent className="p-6 text-white">
                  <div className="flex items-start justify-between gap-3">
                    <div>
                      <p className="text-xs uppercase tracking-[0.25em] text-pink-300/75">Holiday Reminder Engine</p>
                      <h3 className="mt-2 text-2xl font-semibold">Two-month alerts</h3>
                    </div>
                    <Bell className="h-5 w-5 text-pink-300" />
                  </div>
                  <div className="mt-5 space-y-3 text-sm text-white/80">
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Mother’s Day: launch tumblers + self-care gifts</div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Back to School: kids apparel + bottles + decals</div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Halloween: statement tees + pet looks + car decor</div>
                    <div className="rounded-2xl border border-white/10 bg-white/5 p-4">Christmas: ornaments, blankets, candles, socks, gift bundles</div>
                  </div>
                </CardContent>
              </Card>
            </div>
          </div>
        </section>

        <section className="border-y border-white/10 bg-black/30 py-16">
          <div className="mx-auto grid max-w-7xl gap-6 px-6 md:px-10 lg:grid-cols-4">
            {[
              { icon: Crown, title: "Official Logo Branding", text: "Your uploaded IIMNOM logo is the hero identity throughout the site." },
              { icon: Store, title: "POD Sales Focus", text: "Built for shirts, tumblers, pet products, decor, bundles, and branded merch." },
              { icon: Sparkles, title: "Urban Luxury Style", text: "Gold glow, black backgrounds, neon accents, and classy statement visuals." },
              { icon: ShieldCheck, title: "Trust + Clarity", text: "Checkout and legal sections can be expanded with full policies and notices." },
            ].map(({ icon: Icon, title, text }) => (
              <Card key={title} className="rounded-[28px] border border-yellow-300/15 bg-white/5 shadow-none">
                <CardContent className="p-6 text-white">
                  <div className="mb-4 inline-flex rounded-2xl bg-yellow-300/10 p-3 text-yellow-300">
                    <Icon className="h-5 w-5" />
                  </div>
                  <h3 className="text-lg font-semibold">{title}</h3>
                  <p className="mt-3 text-sm leading-6 text-white/70">{text}</p>
                </CardContent>
              </Card>
            ))}
          </div>
        </section>

        <section id="etsy" className="mx-auto max-w-7xl px-6 py-16 md:px-10">
          <SectionHeader
            eyebrow="Etsy Ready Products"
            title="Five starter listings drafted for launch."
            body="These are styled as product-ready concepts you can adapt into Etsy listings. Replace material, size, production, and shipping details with your exact supplier data before publishing."
          />
          <div className="mt-10 grid gap-6 lg:grid-cols-2">
            {etsyReadyProducts.map((item) => (
              <EtsyProductBlock key={item.title} item={item} />
            ))}
          </div>
        </section>

        <section className="border-y border-white/10 bg-black/25">
          <div className="mx-auto grid max-w-7xl gap-6 px-6 py-16 md:px-10 lg:grid-cols-[1fr_1fr]">
            <Card className="rounded-[32px] border border-yellow-300/15 bg-white text-black shadow-lg">
              <CardContent className="p-8">
                <p className="text-xs font-semibold uppercase tracking-[0.26em] text-black/50">Business Identity</p>
                <h3 className="mt-3 text-3xl font-semibold">Letterhead + business cards</h3>
                <div className="mt-6 grid gap-4 md:grid-cols-2">
                  <div className="rounded-[24px] border bg-neutral-50 p-5">
                    <img src={logoImage} alt="IIMNOM logo on letterhead" className="mb-4 h-14 w-14 rounded-full object-cover" />
                    <p className="text-lg font-semibold">IIMNOM</p>
                    <p className="text-sm text-black/65">It’s In Me Not On Me</p>
                    <div className="mt-6 space-y-2 text-sm text-black/70">
                      <p>Kenisha Wilson</p>
                      <p>Owner & Creator</p>
                      <p>iimnom.store@gmail.com</p>
                      <p>#6026546186</p>
                    </div>
                  </div>
                  <div className="rounded-[24px] bg-black p-5 text-white">
                    <img src={logoImage} alt="IIMNOM business card" className="mb-5 h-14 w-14 rounded-full object-cover" />
                    <p className="text-xl font-semibold tracking-[0.15em] text-yellow-300">IIMNOM</p>
                    <p className="mt-1 text-sm text-pink-300">Real Don’t Rub Off</p>
                    <div className="mt-6 space-y-2 text-sm text-white/75">
                      <p>Kenisha Wilson</p>
                      <p>Owner & Creator</p>
                      <p>iimnom.store@gmail.com</p>
                      <p>#6026546186</p>
                    </div>
                  </div>
                </div>
              </CardContent>
            </Card>

            <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
              <CardContent className="p-8 text-white">
                <p className="text-xs font-semibold uppercase tracking-[0.26em] text-yellow-200/70">Suggested Domain</p>
                <h3 className="mt-3 text-3xl font-semibold">iimnomstore.com</h3>
                <div className="mt-6 space-y-4 text-sm leading-6 text-white/75">
                  <p>Also worth checking: iimnomshop.com, shopiimnom.com, iimnombrand.com</p>
                  <ol className="list-decimal space-y-2 pl-5">
                    <li>Buy your domain from a registrar like Namecheap or Squarespace Domains.</li>
                    <li>Build the site in Shopify, Next.js, or a React-based builder with your code.</li>
                    <li>Upload your brand logo, product mockups, policies, and product data.</li>
                    <li>Connect email marketing, supplier products, and payment processing.</li>
                    <li>Publish, test checkout, and launch your first promotion.</li>
                  </ol>
                </div>
                <div className="mt-6 flex flex-wrap gap-3">
                  <Button className="rounded-full bg-white text-black hover:bg-white">Buy Domain</Button>
                  <GlowButton>Launch Setup</GlowButton>
                </div>
              </CardContent>
            </Card>
          </div>
        </section>

        <section className="mx-auto max-w-7xl px-6 py-16 md:px-10">
          <div className="grid gap-6 lg:grid-cols-[0.92fr_1.08fr]">
            <Card className="rounded-[32px] border border-yellow-300/15 bg-[#0d0a0e] shadow-[0_20px_60px_rgba(0,0,0,0.45)]">
              <CardContent className="p-8 text-white">
                <p className="text-xs uppercase tracking-[0.25em] text-yellow-200/70">Checkout Experience</p>
                <h3 className="mt-3 text-3xl font-semibold">Clean, easy billing page</h3>
                <div className="mt-6 space-y-4">
                  <Input placeholder="Full Name" className="rounded-2xl border-white/10 bg-white text-black" />
                  <Input placeholder="Email" className="rounded-2xl border-white/10 bg-white text-black" />
                  <Input placeholder="Shipping Address" className="rounded-2xl border-white/10 bg-white text-black" />
                  <div className="rounded-[24px] border border-white/10 bg-white/5 p-4 text-sm text-white/75">
                    <div className="flex justify-between"><span>Queens Only Tumbler</span><span>$29.99</span></div>
                    <div className="mt-2 flex justify-between"><span>We All We Got Tee</span><span>$29.99</span></div>
                    <div className="mt-2 flex justify-between"><span>Shipping</span><span>$6.95</span></div>
                    <div className="mt-2 flex justify-between"><span>Tax</span><span>$4.88</span></div>
                    <div className="mt-3 flex justify-between border-t border-white/10 pt-3 text-base font-semibold text-yellow-300"><span>Total</span><span>$71.81</span></div>
                  </div>
                  <GlowButton className="w-full">
                    <CreditCard className="mr-2 h-4 w-4" /> Complete Purchase
                  </GlowButton>
                </div>
              </CardContent>
            </Card>

            <Card id="contact" className="rounded-[32px] border border-yellow-300/15 bg-white text-black shadow-lg">
              <CardContent className="p-8">
                <p className="text-xs uppercase tracking-[0.25em] text-black/50">Subscriber Growth</p>
                <h3 className="mt-3 text-3xl font-semibold">Grow your email list and repeat buyers</h3>
                <p className="mt-4 max-w-2xl text-base leading-7 text-black/70">
                  Offer coupons, early-access drops, VIP discount codes, birthday deals, and holiday sale alerts.
                  This is one of the fastest ways to increase profit from repeat traffic.
                </p>
                <div className="mt-6 flex flex-col gap-3 sm:flex-row">
                  <Input
                    value={email}
                    onChange={(e) => setEmail(e.target.value)}
                    placeholder="Enter your email"
                    className="rounded-full"
                  />
                  <GlowButton className="sm:min-w-[220px]">
                    <Mail className="mr-2 h-4 w-4" /> Unlock 15% Off
                  </GlowButton>
                </div>
                <div className="mt-8 grid gap-4 md:grid-cols-3">
                  {[
                    { icon: Mail, title: "Launch Emails" },
                    { icon: Bell, title: "Sale Alerts" },
                    { icon: Megaphone, title: "Social Push" },
                  ].map(({ icon: Icon, title }) => (
                    <div key={title} className="rounded-[22px] bg-neutral-100 p-4">
                      <Icon className="mb-3 h-5 w-5" />
                      <p className="font-medium">{title}</p>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </div>
        </section>
      </main>

      <footer className="border-t border-white/10 bg-black/45">
        <div className="mx-auto grid max-w-7xl gap-6 px-6 py-10 md:px-10 lg:grid-cols-4">
          <div>
            <div className="flex items-center gap-3">
              <img src={logoImage} alt="IIMNOM logo" className="h-12 w-12 rounded-full object-cover" />
              <div>
                <p className="font-semibold tracking-[0.12em] text-white">IIMNOM</p>
                <p className="text-xs uppercase tracking-[0.2em] text-pink-300">Real Don’t Rub Off</p>
              </div>
            </div>
          </div>
          <div className="text-sm text-white/65">
            <p className="font-semibold text-white">Shop</p>
            <p className="mt-2">Apparel</p>
            <p>Tumblers</p>
            <p>Pet Wear</p>
            <p>Home Decor</p>
          </div>
          <div className="text-sm text-white/65">
            <p className="font-semibold text-white">Business</p>
            <p className="mt-2">Kenisha Wilson</p>
            <p>Owner & Creator</p>
            <p>iimnom.store@gmail.com</p>
            <p>#6026546186</p>
          </div>
          <div className="text-sm text-white/65">
            <p className="font-semibold text-white">Brand<
