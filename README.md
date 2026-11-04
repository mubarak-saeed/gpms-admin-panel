# 🎓 نظام إدارة مشاريع التخرج (GPMS)

[![Laravel](https://img.shields.io/badge/Laravel-12.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![Filament](https://img.shields.io/badge/Filament-v5-F59E0B?style=for-the-badge&logo=laravel&logoColor=white)](https://filamentphp.com)
[![Flutter](https://img.shields.io/badge/Flutter-%5E3.38-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-v4.0-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

منصة متكاملة لأتمتة وتنظيم مشاريع التخرج في الكليات والجامعات. يجمع **GPMS** الطلاب
والمشرفين الأكاديميين وإدارة الكلية في منظومة واحدة لتقديم المشاريع، متابعة التقدم،
إدارة المهام والملفات، وتوثيق الاجتماعات والمحادثات.

---

## 🔍 نظرة عامة

يتكون النظام من ثلاثة أجزاء مترابطة:

| الجزء | المسؤولية |
| --- | --- |
| **لوحة الإدارة** | إدارة الكليات والأقسام والسنوات والمشاريع والمشرفين والصلاحيات والتقارير. |
| **تطبيق الجوال** | تمكين الطلاب والمشرفين من متابعة المهام والاجتماعات والملفات والمحادثات. |
| **واجهة REST API** | نقل البيانات بأمان بين التطبيق والخادم باستخدام Laravel Sanctum. |

---

## 📌 الفهرس

- [الميزات الأساسية لكل دور](#-الميزات-الأساسية-لكل-دور)
- [البنية التقنية](#-البنية-التقنية)
- [مخططات النظام](#-مخططات-النظام)
- [الترخيص](#-الترخيص)

---

## 🌟 الميزات الأساسية لكل دور

### 👤 الطالب (قائد وعضو الفريق)

- **إدارة الفرق:** إنشاء فريق أو طلب الانضمام إلى فريق قائم واستقبال الدعوات.
- **تقديم المشاريع:** إرسال مقترح المشروع وطلب الإشراف من الأكاديميين المتاحين.
- **إدارة المهام:** متابعة المهام المسندة وتحديث حالتها حتى الإنجاز.
- **رفع التقارير:** رفع ملفات المشروع وحفظ إصداراتها وتحديد النسخة النهائية.
- **التواصل اللحظي:** الدردشة داخل المشروع مع مشاركة المرفقات واستقبال الإشعارات.
- **مكتبة المشاريع:** البحث في أرشيف مشاريع التخرج السابقة.

### 👨‍🏫 المشرف الأكاديمي

- **طلبات الإشراف:** مراجعة الطلبات وقبولها أو رفضها مع توضيح السبب.
- **متابعة المشاريع:** مراقبة تقدم المشاريع والمهام الخاصة بها.
- **جدولة الاجتماعات:** إنشاء الاجتماعات وتحديد وقتها ومكانها أو رابطها الإلكتروني.
- **الدردشة والمهام:** التواصل مع الفرق وإسناد مهام الطلاب وتحديثها.

### 🛡️ إدارة الجامعة والكليات (الأدمن)

- **التهيئة الأساسية:** إدارة الكليات والأقسام والقيود الأكاديمية للفرق.
- **إدارة السنوات:** تفعيل السنوات الدراسية وأرشفة المشاريع السابقة عند انتهائها.
- **التقارير والإحصائيات:** عرض معدلات الإنجاز وتوزيع نصاب المشرفين والطلاب.
- **التحكم بالصلاحيات:** إدارة الأدوار والصلاحيات باستخدام Spatie وFilament Shield.

---

## 💻 البنية التقنية

### الخلفية ولوحة التحكم (Backend & Admin Panel)

- **الإطار الأساسي:** [Laravel 12.x](https://laravel.com) مع PHP 8.2 أو أحدث.
- **لوحة التحكم:** [Filament v5](https://filamentphp.com) المبنية على Livewire v4.
- **المصادقة:** [Laravel Sanctum](https://laravel.com/docs/12.x/sanctum) لتأمين واجهات API.
- **الصلاحيات:** [Spatie Laravel Permission](https://spatie.be/docs/laravel-permission) و[Filament Shield](https://github.com/bezhanSalleh/filament-shield).
- **البث اللحظي:** [Laravel Reverb](https://laravel.com/docs/12.x/reverb) أو Pusher Channels.

### تطبيق الجوال (Mobile Frontend)

- **إطار العمل:** [Flutter](https://flutter.dev) المتوافق مع SDK `^3.38`.
- **إدارة الحالة:** [Riverpod](https://riverpod.dev).
- **الاتصال بالشبكة:** [Dio](https://pub.dev/packages/dio) مع interceptors للتوكن.
- **التخزين المحلي:** [Hive](https://pub.dev/packages/hive) و[Flutter Secure Storage](https://pub.dev/packages/flutter_secure_storage).
- **المصادقة الحيوية:** دعم البصمة والتعرف على الوجه لتسجيل دخول سريع وآمن.

### قاعدة البيانات والتخزين (Database & Storage)

- **قاعدة البيانات:** MySQL 8.0 أو أحدث مع العلاقات وSoft Deletes.
- **التخزين:** ملفات PDF وZIP وDOCX مع تتبع الإصدارات وصلاحيات الوصول.

---

## 📐 مخططات النظام

> المخططات التالية مكتوبة بصيغة Mermaid وتظهر مباشرة في GitHub ويدعمها الوضعان الفاتح والداكن.

### 1. دورة حياة المشروع

```mermaid
flowchart TD
    A["تسجيل حساب الطالب"] --> B["تكوين فريق أو الانضمام إلى فريق"]
    B --> C["تقديم مقترح مشروع التخرج"]
    C --> D["إرسال طلب إشراف"]
    D --> E{"هل تمت الموافقة؟"}
    E -- "لا" --> F["تعديل المقترح أو اختيار مشرف آخر"]
    E -- "نعم" --> G["تفعيل المشروع وبدء العمل"]
    G --> H["توزيع المهام وجدولة الاجتماعات"]
    H --> I["رفع التقارير والملفات الدورية"]
    I --> J["الاعتماد النهائي من الإدارة"]
    J --> K["أرشفة المشروع وإتاحته في المكتبة"]
```

### 2. العلاقات الكيانية (ERD)

يوضح المخطط العلاقات الرئيسية بين المستخدمين والفرق والمشاريع والمهام والملفات:

```mermaid
erDiagram
    ACADEMIC_YEAR ||--o{ STUDENT : includes
    ACADEMIC_YEAR ||--o{ TEAM : includes
    ACADEMIC_YEAR ||--o{ PROJECT : includes
    COLLEGE ||--o{ DEPARTMENT : contains
    COLLEGE ||--o{ SUPERVISOR : employs
    DEPARTMENT ||--o{ STUDENT : contains
    DEPARTMENT ||--o{ TEAM : contains
    DEPARTMENT ||--o{ PROJECT : contains
    USER ||--o| STUDENT : profile
    USER ||--o| SUPERVISOR : profile
    USER ||--o{ TASK : creates
    USER ||--o{ PROJECT_FILE : uploads
    TEAM ||--o{ TEAM_MEMBER : includes
    TEAM ||--o{ TEAM_REQUEST : receives
    TEAM ||--o| PROJECT : owns
    PROJECT ||--o{ PROJECT_SUPERVISOR : assigns
    PROJECT ||--o{ SUPERVISION_REQUEST : receives
    PROJECT ||--o{ TASK : contains
    PROJECT ||--o{ MEETING : schedules
    PROJECT ||--o| PROJECT_CHAT : has
    PROJECT ||--o{ PROJECT_FILE : stores
    TASK ||--o{ TASK_ASSIGNEE : assigned_to
    PROJECT_CHAT ||--o{ CHAT_MESSAGE : contains
    CHAT_MESSAGE ||--o{ CHAT_ATTACHMENT : includes
    PROJECT_CHAT ||--o{ CHAT_READ_STATE : tracks
```

---

## 📄 الترخيص

هذا المشروع مرخص بموجب [MIT](LICENSE). جميع الحقوق محفوظة لفريق التطوير (Mubarak Saeed).
