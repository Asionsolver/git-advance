```bash
git push -u origin feat/login
To https://github.com/Asionsolver/git-advance.git
! [rejected] feat/login -> feat/login (non-fast-forward)
error: failed to push some refs to 'https://github.com/Asionsolver/git-advance.git '
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

# ⚠️ Troubleshooting: Git Push Rejected (Non-Fast-Forward)

গিটে কাজ করার সময় `! [rejected] feat/login -> feat/login (non-fast-forward)` এররটি অত্যন্ত সাধারণ। এটি মূলত একটি নিরাপত্তা ব্যবস্থা যা আপনার গুরুত্বপূর্ণ কোড অসাবধানতাবশত হারিয়ে যাওয়া থেকে রক্ষা করে।

---

## 🔴 কেন এই এররটি আসে? (The Root Cause)

এই এররটির মূল কারণ হলো—আপনার **Remote Repository (GitHub)**-এ এমন কিছু নতুন কমিট আছে, যা আপনার **Local Machine**-এ নেই।

> [!IMPORTANT]
> **সহজ ভাষায়:** গিট দেখছে যে গিটহাবের ভার্সনটি আপনার কম্পিউটারের ভার্সনের চেয়ে এগিয়ে আছে। আপনি যদি এখন জোর করে পুশ করেন, তবে গিটহাবের সেই নতুন পরিবর্তনগুলো মুছে যেতে পারে। একেই **"Non-fast-forward"** এরর বলা হয়।

---

## 🛠️ সমাধানের ধাপসমূহ (Step-by-Step Solution)

সবচেয়ে নিরাপদ এবং পেশাদার পদ্ধতি হলো প্রথমে রিমোটের পরিবর্তনগুলো নিজের পিসিতে নিয়ে আসা (**Pull**), তারপর সেটিকে নিজের কোডের সাথে মিলিয়ে (**Merge**) পুনরায় পুশ করা।

### ধাপ ১: রিমোট থেকে আপডেট টেনে নিন (Pull)

টার্মিনালে নিচের কমান্ডটি দিন:

```bash
git pull origin feat/login
```

_এটি রিমোটের নতুন কমিটগুলো আপনার লোকাল ব্রাঞ্চের সাথে যুক্ত করার চেষ্টা করবে।_

### ধাপ ২: কনফ্লিক্ট সমাধান (যদি থাকে)

যদি আপনার এবং রিমোটের কোড একই লাইনে থাকে, তবে **Merge Conflict** দেখা দিতে পারে।

1. ফাইলগুলো ওপেন করে কনফ্লিক্ট ম্যানুয়ালি ঠিক করুন।
2. তারপর নিচের কমান্ডগুলো দিয়ে মার্জ সম্পন্ন করুন:

```bash
git add .
git commit -m "Merge remote changes and fix conflicts"
```

### ধাপ ৩: এবার নিরাপদে পুশ করুন

মার্জ হয়ে গেলে এখন আপনি কোনো এরর ছাড়াই পুশ করতে পারবেন:

```bash
git push origin feat/login
```

---

## ⚡ বিকল্প সমাধান: ফোর্স পুশ (Force Push)

যদি আপনি নিশ্চিত হন যে রিমোটের কোড আপনার প্রয়োজন নেই এবং আপনার লোকাল কোডটিই চূড়ান্ত, তবে আপনি জোর করে পুশ করতে পারেন:

```bash
git push -f origin feat/login
```

> [!CAUTION]
> **সতর্কতা:** `--force` বা `-f` ব্যবহার করলে রিমোটের আগের সব ইতিহাস মুছে যাবে। যদি অন্য কোনো ডেভেলপার ওই ব্রাঞ্চে কাজ করে থাকে, তবে তাদের কাজ চিরতরে হারিয়ে যেতে পারে। **টিম প্রজেক্টে এটি এড়িয়ে চলাই শ্রেয়।**

---

## 📌 একনজরে সারসংক্ষেপ (Summary)

| সমস্যা                   | কারণ                               | সমাধান                                   |
| :----------------------- | :--------------------------------- | :--------------------------------------- |
| **Rejected Error**       | লোকাল ব্রাঞ্চ রিমোটের চেয়ে পিছিয়ে। | `git pull` করে আপডেট নিন।                |
| **Non-fast-forward**     | সরাসরি ওভাররাইট করা সম্ভব নয়।      | মার্জ সম্পন্ন করে তারপর `git push` করুন। |
| **Data Loss Prevention** | গিট আপনার কোড রক্ষা করছে।          | রিমোট ও লোকাল কোড সিঙ্ক (Sync) করুন।     |

---

## ✅ সেরা অভ্যাস (Best Practice)

পুশ করার আগে সবসময় একটি `git pull` দিয়ে নেওয়া একটি ভালো অভ্যাস। এতে কনফ্লিক্ট হওয়ার সম্ভাবনা কমে যায় এবং আপনার লোকাল কোডবেস সবসময় রিমোটের সাথে আপ-টু-ডেট থাকে।

---

_আপনার কোডিং যাত্রা শুভ হোক!_ 🚀✨
