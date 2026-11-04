# 🎓 نظام إدارة مشاريع التخرج (GPMS)

<p align="center">
  <a href="https://laravel.com"><img src="https://img.shields.io/badge/Laravel-13.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel"></a>
  <a href="https://filamentphp.com"><img src="https://img.shields.io/badge/Filament-v5-F59E0B?style=for-the-badge&logo=laravel&logoColor=white" alt="Filament"></a>
  <a href="https://flutter.dev"><img src="https://img.shields.io/badge/Flutter-%5E3.38-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter"></a>
  <a href="https://tailwindcss.com"><img src="https://img.shields.io/badge/TailwindCSS-v4.0-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS"></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge" alt="MIT License"></a>
</p>

<div dir="rtl" align="right">

## ✨ نظرة عامة عن النظام 

**GPMS** منصة رقمية متكاملة لإدارة مشاريع التخرج داخل الكليات والجامعات، وتربط بين الطالب، والمشرف الأكاديمي، وإدارة الجامعة ضمن دورة عمل موحدة وواضحة تشمل:

- تقديم واعتماد المقترحات
- تنظيم فرق المشاريع
- متابعة المهام والاجتماعات
- إدارة الملفات والإصدارات
- التواصل الفوري والتوثيق الأكاديمي

---

## 📌 الفهرس

- [نظرة عامة على مكونات النظام](#-نظرة-عامة-على-مكونات-النظام)
- [الميزات الأساسية حسب الأدوار](#-الميزات-الأساسية-حسب-الأدوار)
- [البنية التقنية](#-البنية-التقنية)
- [مخططات Mermaid](#-مخططات-mermaid)
- [الترخيص](#-الترخيص)

---

## 🔍  مكونات النظام

يتكون النظام من ثلاثة مكونات مترابطة:

| المكوّن | الدور |
| --- | --- |
| **لوحة الإدارة** | إدارة الكليات والأقسام والسنوات الأكاديمية والمشاريع والصلاحيات والتقارير. |
| **تطبيق الجوال** | دعم الطالب والمشرف في متابعة المهام والاجتماعات والملفات والتواصل اليومي. |
| **واجهة REST API** | وسيط آمن بين الواجهة الخلفية وتطبيق الجوال باستخدام Laravel Sanctum. |

---

## 🌟 الميزات الأساسية حسب الأدوار

### 👤 الطالب (قائد الفريق / عضو الفريق)

- إنشاء فريق جديد أو الانضمام إلى فريق قائم.
- تقديم مقترح مشروع التخرج وطلب الإشراف الأكاديمي.
- متابعة المهام وتحديث حالاتها حتى الإغلاق.
- رفع تقارير وملفات المشروع مع تتبع الإصدارات.
- التواصل الفوري داخل المشروع مع دعم المرفقات والإشعارات.
- الاستفادة من مكتبة المشاريع المؤرشفة.

### 👨‍🏫 المشرف الأكاديمي

- مراجعة طلبات الإشراف والقبول أو الرفض مع المبررات.
- متابعة تقدم الفرق والمشاريع المرتبطة به.
- تنظيم الاجتماعات حضوريًا أو عبر روابط إلكترونية.
- إدارة المهام وتوزيعها على أعضاء الفرق.

### 🛡️ إدارة الجامعة والكليات

- ضبط الهيكل الأكاديمي (الكليات، الأقسام، السنوات).
- تفعيل/أرشفة السنوات الدراسية ومشاريعها.
- مراقبة المؤشرات والتقارير والإحصائيات التشغيلية.
- إدارة الأدوار والصلاحيات عبر Spatie وFilament Shield.

---

## 💻 البنية التقنية

### Backend & Admin Panel

- **Laravel 12.x** مع **PHP 8.2+**
- **Filament v5** مبني على **Livewire v4**
- **Laravel Sanctum** للمصادقة وتأمين الواجهات
- **Spatie Laravel Permission** + **Filament Shield** لإدارة الصلاحيات
- **Laravel Reverb** أو **Pusher** للبث اللحظي

### Mobile App

- **Flutter** (SDK `^3.38`)
- **Riverpod** لإدارة الحالة
- **Dio** للاتصال بالشبكة وإدارة التوكن
- **Hive** و **Flutter Secure Storage** للتخزين المحلي

### Database & Storage

- **MySQL 8+** مع العلاقات وSoft Deletes
- إدارة ملفات المشروع (PDF/ZIP/DOCX) مع تتبع النسخ وصلاحيات الوصول

---

## 📐 بعض مخططات النظام

### 1) دورة حياة المشروع

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

### 2) العلاقات الكيانية (ERD)

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

هذا المشروع مرخص بموجب [MIT](LICENSE).

</div>
