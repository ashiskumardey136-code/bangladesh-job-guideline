# বাংলাদেশ জব গাইড লাইন (Bangladesh Job Guideline)

সরকারি ও বেসরকারি চাকরির আবেদন প্রক্রিয়া, যোগ্যতা, বয়সসীমা, পরীক্ষার ধাপ এবং প্রস্তুতির
সঠিক দিকনির্দেশনা এক জায়গায় দেওয়ার জন্য তৈরি একটি প্রফেশনাল Flutter অ্যাপ।

## প্রজেক্ট স্ট্রাকচার
```
bd_job_guideline/
├── android/                     # Android platform ফোল্ডার (flutter create দিয়ে অটো তৈরি হবে)
├── assets/
│   └── guidelines.json          # সব গাইডলাইন ডেটা এখানে সংরক্ষিত
├── lib/
│   ├── main.dart                # অ্যাপের থিম ও এন্ট্রি পয়েন্ট
│   ├── models/
│   │   └── guideline.dart       # Guideline ডেটা মডেল
│   ├── data/
│   │   └── guideline_repository.dart  # JSON লোড ও পার্স করার লজিক
│   └── screens/
│       ├── home_screen.dart           # ক্যাটাগরি অনুযায়ী গাইডলাইন লিস্ট
│       └── guideline_detail_screen.dart # বিস্তারিত গাইডলাইন স্ক্রিন
├── pubspec.yaml
└── .gitignore
```

## ধাপ ১: প্রজেক্ট চালু করা
এই ফাইলগুলো একটি নতুন Flutter প্রজেক্টের ওপর বসাতে হবে, কারণ `android/`, `ios/` ইত্যাদি
প্ল্যাটফর্ম ফোল্ডার এখানে দেওয়া নেই (এগুলো অনেক বড় ও অটো-জেনারেটেড)।

```bash
flutter create bd_job_guideline
cd bd_job_guideline
# এই রিপোজিটরির lib/, assets/, pubspec.yaml কপি করে বসিয়ে দিন
flutter pub get
flutter run
```

## ধাপ ২: নতুন গাইডলাইন যোগ করা
`assets/guidelines.json` ফাইলে নিচের ফরম্যাটে নতুন এন্ট্রি যোগ করুন:
```json
{
  "id": "ntrca-2026",
  "category": "শিক্ষকতা",
  "title": "১৯তম NTRCA নিবন্ধন",
  "eligibility": "স্নাতক পাস, বয়স ২১-৩৫",
  "steps": ["আবেদন ফরম পূরণ", "পরীক্ষার ফি জমা", "প্রবেশপত্র ডাউনলোড"],
  "deadline": "যাচাই করে নিন সংশ্লিষ্ট ওয়েবসাইটে",
  "source_note": "তথ্য পরিবর্তনযোগ্য, সর্বশেষ সার্কুলার দেখে নিশ্চিত হোন"
}
```

## GitHub-এ প্রফেশনালভাবে সেট আপ করার ধাপ

1. GitHub-এ নতুন রিপোজিটরি খুলুন: `bd-job-guideline`
2. রিপো তৈরির সময় **README যোগ করবেন না** (আমাদের কাস্টম README আছে) — শুধু `.gitignore`
   টেমপ্লেট হিসেবে Flutter বেছে নিতে পারেন, অথবা নিচের `.gitignore` ব্যবহার করুন
3. এই ফোল্ডারের সব ফাইল রিপোতে push করুন:
   ```bash
   git init
   git add .
   git commit -m "Initial professional project structure"
   git branch -M main
   git remote add origin https://github.com/<your-username>/bd-job-guideline.git
   git push -u origin main
   ```
4. রিপোর **Settings → Branches**-এ গিয়ে `main` ব্রাঞ্চের জন্য branch protection চালু করুন
   (পরে টিমে কাজ করলে দরকার হবে)
5. নতুন ফিচার আনার সময় সবসময় আলাদা ব্রাঞ্চ খুলুন (যেমন `feature/dark-mode`), তারপর
   `compare: feature/dark-mode` বেছে Pull Request বানান — `main` বনাম `main` কম্পেয়ার
   করলে GitHub "There isn't anything to compare" দেখাবে, কারণ একই ব্রাঞ্চ

## সততা সংক্রান্ত নোট
সার্কুলারের তারিখ, বয়সসীমা ও যোগ্যতা সময়ের সাথে বদলায়। অ্যাপে সবসময় "সর্বশেষ সার্কুলার
যাচাই করুন" জাতীয় স্পষ্ট বার্তা রাখা হয়েছে, যাতে ইউজার ভুল তথ্যের ওপর নির্ভর না করে ফেলেন।

## পরবর্তী উন্নতির আইডিয়া
- ক্যাটাগরি ফিল্টার (শিক্ষকতা, ব্যাংক, BCS, প্রতিরক্ষা ইত্যাদি)
- পুশ নোটিফিকেশন দিয়ে ডেডলাইন রিমাইন্ডার
- বুকমার্ক/ফেভারিট গাইডলাইন সেভ করার ফিচার
