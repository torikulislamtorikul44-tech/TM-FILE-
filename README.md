# TM FILE - Android File Manager App (Kotlin + Jetpack Compose)

আধুনিক অ্যান্ড্রয়েড আর্কিটেকচার (MVVM, Kotlin Coroutines, StateFlow) এবং **Jetpack Compose (Material 3)** দিয়ে তৈরি একটি পূর্ণাঙ্গ **TM FILE** ফাইল ম্যানেজার অ্যাপ্লিকেশন।

---

## 📱 ফিচারসমূহ (Features)

1. **ড্যাশবোর্ড ও স্টোরেজ ওভারভিউ (Storage Dashboard):**
   - ইন্টারনাল স্টোরেজের মোট স্পেস, ব্যবহৃত স্পেস ও ফাঁকা স্পেসের ভিজ্যুয়াল প্রগ্রেস বার।
   - শতাংশ হিসাব (Storage Percentage Used)।
2. **ক্যাটাগরি ব্রাউজার (Category Explorer):**
   - ফাইল ক্যাটাগরি অনুযায়ী ফিল্টারিং:
     - 🖼️ Images (ছবি)
     - 🎥 Videos (ভিডিও)
     - 🎵 Audio (অডিও/গান)
     - 📄 Documents (পিডিএফ, ডক, টেক্সট ইত্যাদি)
     - 📦 APKs (অ্যাপ্লিকেশন প্যাকেজ)
     - 🗜️ Archives (জিপ, রার ফাইল)
3. **ফাইল এক্সপ্লোরার (Full File Explorer):**
   - ডিরেক্টরি অনুযায়ী ব্রাউজিং ও সাব-ফোল্ডার নেভিগেশন।
   - **ইন্টারেক্টিভ ব্রেডক্রাম্ব (Breadcrumbs):** যেকোনো প্যারেন্ট ফোল্ডারে এক ক্লিকে ফিরে যাওয়ার সুবিধা (`Storage > Download > ...`)।
   - ছবির লাইভ থাম্বনেইল প্রিভিউ (Coil লাইব্রেরির মাধ্যমে)।
   - প্রতিটি আইটেমের সাইজ, মডিফাইড তারিখ ও আইটেম কাউন্ট প্রদর্শন।
4. **ফাইল অপারেশনস (File Operations):**
   - 📁 নতুন ফোল্ডার তৈরি (Create New Folder)।
   - ✏️ রিনেম (Rename File/Folder)।
   - 🗑️ ডিলিট (Delete with confirmation)।
   - 📋 কপি ও মুভ/কাট (Copy & Cut with Floating Paste Bar)।
   - 📤 ফাইল শেয়ার (Share via Intent)।
   - 🚀 ফাইল ওপেন (FileProvider ও সংশ্লিষ্ট অ্যাপ দিয়ে ওপেন)।
   - ℹ️ ফাইল ডিটেইলস (Properties: Path, Size, Permissions, Last Modified)।
5. **ইনস্ট্যান্ট সার্চ (Search):**
   - দ্রুত যেকোনো ফাইল বা ফোল্ডার নাম দিয়ে খোঁজার সুবিধা।
6. **সর্টিং (Sorting):**
   - নাম অনুসারে (A to Z / Z to A)
   - সাইজ অনুসারে (ছোট থেকে বড় / বড় থেকে ছোট)
   - তারিখ অনুসারে (নতুন থেকে পুরানো / পুরানো থেকে নতুন)
7. **পারমিশন ম্যানেজমেন্ট (Scoped Storage & All Files Access):**
   - অ্যান্ড্রয়েড ১১+ (API 30+) এর জন্য `MANAGE_EXTERNAL_STORAGE` সাপোর্ট।
   - অ্যান্ড্রয়েড ১০ ও তার আগের জন্য রিড/রাইট পারমিশন হ্যান্ডলিং।

---

## 🏗️ আর্কিটেকচার ও টেক স্ট্যাক (Tech Stack)

- **Language:** Kotlin
- **UI Framework:** Jetpack Compose (Material 3)
- **Architecture:** MVVM (Model-View-ViewModel) + Clean Architecture
- **State Management:** Kotlin StateFlow & Coroutines
- **Navigation:** Jetpack Navigation Compose
- **Image Loading:** Coil Compose
- **Build System:** Gradle (Kotlin DSL - `.gradle.kts`)
- **Min SDK:** 26 (Android 8.0+)
- **Target SDK:** 34 (Android 14)

---

## 📂 প্রোজেক্টের ফোল্ডার স্ট্রাকচার (Project Structure)

```
FileManagerApp/
├── app/
│   ├── src/main/
│   │   ├── AndroidManifest.xml          # পারমিশন ও ফাইলপ্রোভাইডার কনফিগারেশন
│   │   ├── res/                         # কালার, স্ট্রিংস ও থিম রিসোর্স
│   │   └── java/com/example/filemanager/
│   │       ├── MainActivity.kt          # মেইন অ্যাক্টিভিটি ও নেভিগেশন হোস্ট
│   │       ├── data/
│   │       │   ├── model/               # FileItem, FileType, StorageInfo, SortOption
│   │       │   └── repository/          # FileRepository (অ্যাসিনক্রোনাস ফাইল অপারেশন)
│   │       ├── ui/
│   │       │   ├── theme/               # Material 3 থিম, কালার ও টাইপোগ্রাফি
│   │       │   ├── components/          # StorageCard, FileListItem, BreadcrumbBar, ইত্যাদি
│   │       │   ├── screens/             # HomeScreen, ExplorerScreen, CategoryFilesScreen, SearchScreen
│   │       │   └── viewmodel/           # FileManagerViewModel (স্টেট ম্যানেজমেন্ট)
│   │       └── utils/                   # FileUtils (MIME, Intent, সাইজ ফরম্যাটিং) ও PermissionUtils
├── build.gradle.kts
└── settings.gradle.kts
```

---

## 🚀 কীভাবে প্রোজেক্টটি চালাবেন (How to Run)

### ১. অ্যান্ড্রয়েড স্টুডিও (Android Studio) ইনস্টল করুন:
যদি আপনার পিসিতে অ্যান্ড্রয়েড স্টুডিও না থাকে, তবে [developer.android.com/studio](https://developer.android.com/studio) থেকে **Android Studio** ডাউনলোড ও ইনস্টল করে নিন।

### ২. প্রোজেক্ট ওপেন করুন:
1. অ্যান্ড্রয়েড স্টুডিও চালু করুন।
2. **Open** অপশনে ক্লিক করুন।
3. নিচের ফোল্ডার পাথটি সিলেক্ট করুন:
   ```
   C:\Users\Torikul\Desktop\CAUDE AI\FileManagerApp
   ```
4. অ্যান্ড্রয়েড স্টুডিও স্বয়ংক্রিয়ভাবে Gradle সিঙ্ক সম্পন্ন করবে।

### ৩. অ্যাপ রান করুন:
1. অ্যান্ড্রয়েড স্টুডিও থেকে একটি **Emulator** রান করুন অথবা আপনার মোবাইল ফোনে **USB Debugging** অন করে ক্যাবল দিয়ে কানেক্ট করুন।
2. স্টুডিওর উপরের সবুজ **Run (▶)** বাটনে ক্লিক করুন।
3. অ্যাপটি ফোনে ইনস্টল হলে প্রথমবার "Storage Permission Required" দেখাবে, সেখানে **Grant Permission** এ ক্লিক করে "All files access" অনুমতিটি চালু করে দিন।
