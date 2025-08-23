import React, { useMemo, useRef, useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { Play, Pause, ChevronLeft, ChevronRight, Youtube, ScrollText, Download } from "lucide-react";
import { Card, CardContent, CardHeader, CardTitle, CardDescription } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Badge } from "@/components/ui/badge";
import { Progress } from "@/components/ui/progress";

// 👇 Replace this with your actual MP4 file path or URL
const VIDEO_SRC = "/videos/oats-cup.mp4";

export default function OatsCupRecipeSite() {
  const steps = useMemo(
    () => [
      {
        title: "ওটস কাপ কীভাবে বানাবেন – ধাপ ১",
        desc: "একটি বাটিতে ১/২ কাপ ইনস্ট্যান্ট ওটস, ১ টেবিল চামচ কোকো পাউডার (ঐচ্ছিক), ১–২ টেবিল চামচ চিনি/মধু, এক চিমটি লবণ মিশিয়ে নিন।",
        tip: "স্বাস্থ্যকর রাখতে খেজুরের গুড় বা মধু ব্যবহার করতে পারেন।",
      },
      {
        title: "ধাপ ২",
        desc: "এবার দিন ১/২ কাপ দুধ (বা প্লান্ট মিল্ক) ও ১ টেবিল চামচ দই/পিনাট বাটার। ভালোভাবে নেড়ে ব্যাটার বানান।",
        tip: "ব্যাটার বেশি ঘন হলে ১–২ টেবিল চামচ দুধ বাড়িয়ে দিন।",
      },
      {
        title: "ধাপ ৩",
        desc: "আপনার প্রিয় একটি মাইক্রোওয়েভ সেফ কাপ/রেমেকিনে মিশ্রণ ঢালুন। উপরে চকলেট চিপস/বাদাম/কিশমিশ ছড়িয়ে দিন।",
        tip: "কাপের ২/৩ এর বেশি ভরবেন না—স্ফীত হবে।",
      },
      {
        title: "ধাপ ৪",
        desc: "মাইক্রোওয়েভে ১ মিনিট চালান। তারপর 10–15 সেকেন্ড করে চেক করতে করতে ১:৩০–২:০০ মিনিট পর্যন্ত রান করুন—সেট হয়ে গেলে বের করুন।",
        tip: "ওভারকুক করবেন না—শুকিয়ে যাবে। সেন্টার সামান্য নরম থাকলে পারফেক্ট।",
      },
      {
        title: "ধাপ ৫",
        desc: "২ মিনিট ঠান্ডা হতে দিন, উপরে দই/ফল/মধু দিয়ে সার্ভ করুন।",
        tip: "স্ট্রবেরি/কলা স্লাইস দারুণ যায়!",
      },
    ],
    []
  );

  const [index, setIndex] = useState(0);
  const videoRef = useRef(null);
  const progress = ((index + 1) / steps.length) * 100;

  const next = () => setIndex((i) => (i + 1) % steps.length);
  const prev = () => setIndex((i) => (i - 1 + steps.length) % steps.length);

  const scrollToVideo = () => {
    const el = document.getElementById("video-section");
    el?.scrollIntoView({ behavior: "smooth", block: "start" });
  };

  const downloadRecipe = () => {
    const text = `ওটস কাপ রেসিপি\n\nউপকরণ:\n- ১/২ কাপ ইনস্ট্যান্ট ওটস\n- ১ টেবিল চামচ কোকো পাউডার (ঐচ্ছিক)\n- ১–২ টেবিল চামচ চিনি/মধু\n- এক চিমটি লবণ\n- ১/২ কাপ দুধ (বা প্লান্ট মিল্ক)\n- ১ টেবিল চামচ দই/পিনাট বাটার\n- টপিংস: চকলেট চিপস/বাদাম/কিশমিশ\n\nপদ্ধতি:\n1) শুকনা উপকরণ মেশান।\n2) দুধ ও দই/পিনাট বাটার দিয়ে ব্যাটার বানান।\n3) মিশ্রণ কাপ/রেমেকিনে ঢালুন, টপিংস দিন।\n4) মাইক্রোওয়েভ ১:৩০–২:০০ মিনিট, মাঝে চেক করুন।\n5) ২ মিনিট বিশ্রাম, টপিংস দিয়ে পরিবেশন।`;
    const blob = new Blob([text], { type: "text/plain;charset=utf-8" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = "oats-cup-recipe-bn.txt";
    a.click();
    URL.revokeObjectURL(url);
  };

  return (
    <div className="min-h-screen w-full bg-gradient-to-b from-amber-50 to-orange-50 text-slate-800">
      {/* Header */}
      <header className="sticky top-0 z-30 backdrop-blur bg-white/70 border-b border-amber-200/60">
        <div className="max-w-5xl mx-auto px-4 py-3 flex items-center justify-between">
          <div className="flex items-center gap-3">
            <span className="inline-flex h-10 w-10 items-center justify-center rounded-2xl bg-amber-200/70 shadow">
              🥣
            </span>
            <div>
              <h1 className="text-xl sm:text-2xl font-bold">ওটস কাপ রেসিপি</h1>
              <p className="text-xs sm:text-sm text-slate-600">দ্রুত, হালকা ও স্বাস্থ্যকর প্রাতঃরাশ/স্ন্যাক</p>
            </div>
          </div>

          <div className="hidden sm:flex items-center gap-2">
            <Button variant="secondary" className="rounded-2xl" onClick={downloadRecipe}>
              <Download className="h-4 w-4 mr-2" /> রেসিপি ডাউনলোড
            </Button>
            <Button className="rounded-2xl" onClick={scrollToVideo}>
              <Youtube className="h-4 w-4 mr-2" /> ভিডিও দেখুন
            </Button>
          </div>
        </div>
      </header>

      {/* Content */}
      <main className="max-w-5xl mx-auto px-4 py-6 grid grid-cols-1 lg:grid-cols-3 gap-6">
        {/* Presentation / Steps */}
        <Card className="lg:col-span-2 rounded-2xl shadow-sm">
          <CardHeader className="pb-2">
            <CardTitle className="text-lg sm:text-xl">স্টেপ-বাই-স্টেপ প্রেজেন্টেশন</CardTitle>
            <CardDescription>স্লাইড করে ধাপ পরিবর্তন করুন</CardDescription>
            <div className="mt-3"><Progress value={progress} className="h-2" /></div>
          </CardHeader>
          <CardContent>
            <div className="relative overflow-hidden rounded-2xl border bg-white">
              <div className="absolute inset-y-0 left-0 flex items-center p-2">
                <Button variant="secondary" size="icon" className="rounded-2xl" onClick={prev} aria-label="আগের স্লাইড">
                  <ChevronLeft className="h-5 w-5" />
                </Button>
              </div>
              <div className="absolute inset-y-0 right-0 flex items-center p-2">
                <Button variant="secondary" size="icon" className="rounded-2xl" onClick={next} aria-label="পরের স্লাইড">
                  <ChevronRight className="h-5 w-5" />
                </Button>
              </div>

              <div className="px-5 py-8 min-h-[220px] flex items-center justify-center">
                <AnimatePresence mode="wait">
                  <motion.div
                    key={index}
                    initial={{ opacity: 0, x: 40 }}
                    animate={{ opacity: 1, x: 0 }}
                    exit={{ opacity: 0, x: -40 }}
                    transition={{ duration: 0.35 }}
                    className="text-center max-w-2xl"
                  >
                    <h3 className="text-lg sm:text-xl font-bold mb-2">{steps[index].title}</h3>
                    <p className="text-sm sm:text-base leading-relaxed mb-3">{steps[index].desc}</p>
                    <Badge variant="secondary" className="text-xs">💡 টিপ: {steps[index].tip}</Badge>
                    <div className="mt-5 text-xs text-slate-500">স্লাইড {index + 1} / {steps.length}</div>
                  </motion.div>
                </AnimatePresence>
              </div>
            </div>
          </CardContent>
        </Card>

        {/* Ingredients & Info */}
        <Card className="rounded-2xl shadow-sm">
          <CardHeader className="pb-2">
            <CardTitle className="text-lg sm:text-xl">উপকরণ</CardTitle>
            <CardDescription>১ কাপ = ২৪০ মি.লি.</CardDescription>
          </CardHeader>
          <CardContent>
            <ul className="space-y-2 text-sm sm:text-base">
              <li>• ১/২ কাপ ইনস্ট্যান্ট ওটস</li>
              <li>• ১ টেবিল চামচ কোকো পাউডার (ঐচ্ছিক)</li>
              <li>• ১–২ টেবিল চামচ চিনি/মধু</li>
              <li>• এক চিমটি লবণ</li>
              <li>• ১/২ কাপ দুধ (বা প্লান্ট মিল্ক)</li>
              <li>• ১ টেবিল চামচ দই/পিনাট বাটার</li>
              <li>• টপিংস: চকলেট চিপস/বাদাম/কিশমিশ</li>
            </ul>
            <div className="mt-5 grid grid-cols-2 gap-3 text-xs sm:text-sm">
              <div className="p-3 rounded-xl bg-amber-100/60">⏱️ সময়: ~৫–৭ মিনিট</div>
              <div className="p-3 rounded-xl bg-amber-100/60">🍽️ সার্ভিং: ১</div>
              <div className="p-3 rounded-xl bg-amber-100/60">🔥 পদ্ধতি: মাইক্রোওয়েভ</div>
              <div className="p-3 rounded-xl bg-amber-100/60">🥛 ডেইরি-ফ্রি বিকল্প আছে</div>
            </div>
          </CardContent>
        </Card>

        {/* Tips */}
        <Card className="lg:col-span-3 rounded-2xl shadow-sm">
          <CardHeader>
            <CardTitle className="text-lg sm:text-xl">অতিরিক্ত টিপস</CardTitle>
            <CardDescription>স্বাদ ও টেক্সচার উন্নত করুন</CardDescription>
          </CardHeader>
          <CardContent className="grid sm:grid-cols-2 lg:grid-cols-4 gap-3">
            <div className="p-4 rounded-2xl bg-white border">
              <p className="text-sm">✨ বেকিং পাউডার ১/৪ চা-চামচ দিলে আরো ফ্লাফি হবে।</p>
            </div>
            <div className="p-4 rounded-2xl bg-white border">
              <p className="text-sm">🌰 টপিংসে বাদাম/চিয়া/ফ্ল্যাক্স দিলে পুষ্টি বাড়বে।</p>
            </div>
            <div className="p-4 rounded-2xl bg-white border">
              <p className="text-sm">🍫 কোকো ছাড়া ভ্যানিলা এসেন্স দিলে ভ্যানিলা ওটস কাপ হবে।</p>
            </div>
            <div className="p-4 rounded-2xl bg-white border">
              <p className="text-sm">🧊 মিল-প্রেপ: শুকনা মিক্স আগে থেকে জারে বানিয়ে রাখুন।</p>
            </div>
          </CardContent>
        </Card>

        {/* Video Section */}
        <section id="video-section" className="lg:col-span-3">
          <Card className="rounded-2xl shadow-sm">
            <CardHeader>
              <div className="flex items-center justify-between">
                <div>
                  <CardTitle className="text-lg sm:text-xl">ভিডিও প্লেয়ার</CardTitle>
                  <CardDescription>ধাপগুলো ভিডিওতে দেখুন</CardDescription>
                </div>
                <div className="hidden sm:flex gap-2">
                  <Button variant="secondary" className="rounded-2xl" onClick={() => videoRef.current?.play()}>
                    <Play className="h-4 w-4 mr-2" /> প্লে
                  </Button>
                  <Button variant="secondary" className="rounded-2xl" onClick={() => videoRef.current?.pause()}>
                    <Pause className="h-4 w-4 mr-2" /> পজ
                  </Button>
                </div>
              </div>
            </CardHeader>
            <CardContent>
              <div className="aspect-video w-full overflow-hidden rounded-2xl border bg-black/5">
                <video
                  ref={videoRef}
                  controls
                  className="w-full h-full object-cover"
                  src={VIDEO_SRC}
                  poster="/images/oats-cup-poster.jpg"
                >
                  আপনার ব্রাউজার ভিডিও ট্যাগ সাপোর্ট করে না।
                </video>
              </div>
              <p className="text-xs text-slate-500 mt-2">
                টিপ: আপনার নিজের ভিডিও ফাইল যুক্ত করতে <code>VIDEO_SRC</code> কনস্ট্যান্টে URL/পাথ বসিয়ে দিন।
              </p>
            </CardContent>
          </Card>
        </section>
      </main>

      {/* Footer */}
      <footer className="max-w-5xl mx-auto px-4 pb-10">
        <div className="mt-6 flex flex-col sm:flex-row items-center justify-between gap-3 text-xs text-slate-600">
          <div className="flex items-center gap-2">
            <ScrollText className="h-4 w-4" />
            <span>কনটেন্ট বেশি হলে পেজ স্বাভাবিকভাবেই স্ক্রল হবে।</span>
          </div>
          <div>© {new Date().getFullYear()} Oats Cup • বানানো হলো ভালোবাসায় 🧡</div>
        </div>
      </footer>
    </div>
  );
}
