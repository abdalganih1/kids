### **أولاً: تعليمات إنشاء بنية المجلدات والملفات في Git Bash**

افتح Git Bash في جذر مشروع Flutter الخاص بك ونفّذ الأوامر التالية خطوة بخطوة:

```bash
# إنشاء المجلدات الأساسية
mkdir -p lib/config lib/models lib/providers lib/screens lib/l10n

# إنشاء ملفات التهيئة (config)
touch lib/config/env.dart

# إنشاء ملفات النماذج (models)
touch lib/models/admin_model.dart
touch lib/models/announcement_model.dart
touch lib/models/attendance_model.dart
touch lib/models/child_meal_status_model.dart
touch lib/models/child_model.dart
touch lib/models/daily_meal_model.dart
touch lib/models/educational_resource_model.dart
touch lib/models/event_model.dart
touch lib/models/event_registration_model.dart
touch lib/models/health_record_model.dart
touch lib/models/kindergarten_class_model.dart
touch lib/models/media_model.dart
touch lib/models/message_model.dart
touch lib/models/observation_model.dart
touch lib/models/parent_model.dart
touch lib/models/weekly_schedule_model.dart
touch lib/models/user_model.dart # هذا يجب أن يكون الأخير لأنه يعتمد على Parent و Admin

# إنشاء ملفات الـ Providers (فارغة في هذا الحل لكن جاهزة للاستخدام لاحقًا)
mkdir -p lib/providers/auth
mkdir -p lib/providers/children
mkdir -p lib/providers/home_data
touch lib/providers/auth/auth_provider.dart
touch lib/providers/children/children_provider.dart
touch lib/providers/home_data/home_data_provider.dart


# إنشاء ملفات الشاشات (screens)
mkdir -p lib/screens/authentication
mkdir -p lib/screens/main_sections
mkdir -p lib/screens/child_features
mkdir -p lib/screens/educational_games
mkdir -p lib/screens/notifications
mkdir -p lib/screens/messaging

touch lib/screens/authentication/login_screen.dart
touch lib/screens/authentication/signup_screen.dart
touch lib/screens/main_sections/home_page.dart
touch lib/screens/main_sections/weekly_schedule_page.dart # WeeklyPage.txt -> weekly_schedule_page.dart

touch lib/screens/child_features/child_profile_screen.dart # profile.txt -> child_profile_screen.dart
touch lib/screens/child_features/attendance_log_screen.dart # Check.txt -> attendance_log_screen.dart
touch lib/screens/child_features/health_dashboard_page.dart # healthe.txt -> health_dashboard_page.dart
touch lib/screens/child_features/health_records_timeline_screen.dart # Health-record.txt -> health_records_timeline_screen.dart
touch lib/screens/child_features/daily_meal_record_page.dart # eat.txt -> daily_meal_record_page.dart
touch lib/screens/child_features/student_activity_schedule_page.dart # activity.txt -> student_activity_schedule_page.dart
touch lib/screens/child_features/student_media_gallery_screen.dart # gallery.txt -> student_media_gallery_screen.dart
touch lib/screens/child_features/educational_resources_list_screen.dart # book.txt -> educational_resources_list_screen.dart
touch lib/screens/child_features/upcoming_events_mobile_screen.dart # events.txt -> upcoming_events_mobile_screen.dart
touch lib/screens/child_features/teacher_notes_display_page.dart # note.txt -> teacher_notes_display_page.dart
touch lib/screens/child_features/class_overview_screen.dart # class.txt -> class_overview_screen.dart

touch lib/screens/educational_games/games_gallery.dart # playes.txt -> games_gallery.dart
touch lib/screens/educational_games/bubble_pop_game.dart # BubblePopplay.txt -> bubble_pop_game.dart
touch lib/screens/educational_games/counting_game.dart # connectplay.txt -> counting_game.dart
touch lib/screens/educational_games/coloring_game.dart # colorplay.txt -> coloring_game.dart
touch lib/screens/educational_games/drag_and_drop_game.dart # DragDropplay.txt -> drag_and_drop_game.dart
touch lib/screens/educational_games/memory_game_page.dart # memoryplay.txt -> memory_game_page.dart
touch lib/screens/educational_games/maze_game.dart # sequenceplay.txt -> maze_game.dart


# إنشاء ملفات الرسائل (messaging)
touch lib/screens/messaging/compose_message_screen.dart # message.txt -> compose_message_screen.dart
touch lib/screens/messaging/email_detail_screen.dart # text_message.txt -> email_detail_screen.dart
touch lib/screens/messaging/gmail_inbox_screen.dart # TeacherContact.txt -> gmail_inbox_screen.dart (اسم جديد أكثر دقة)

# إنشاء ملفات رئيسية
touch lib/main.dart
touch lib/start_app.dart # start.txt -> start_app.dart ( لتجنب تضارب الاسم مع package:start )

# حذف ملفات temp قديمة أو غير مستخدمة (اختياري، إذا كنت نقلت محتويات من ملفات موجودة)
# rm lib/Check.dart lib/Health-record.dart lib/TeacherContact.dart lib/WeeklyPage.dart lib/activity.dart lib/book.dart lib/class.dart lib/colorplay.dart lib/connectplay.dart lib/day_program.txt lib/DragDropplay.txt lib/eat.txt lib/events.txt lib/ex.txt lib/ex1.txt lib/gallery.txt lib/gmail_inbox_screen.txt lib/healthe.txt lib/home.dart lib/login.dart lib/memoryplay.txt lib/message.txt lib/note.txt lib/playes.txt lib/profile.dart lib/sequenceplay.txt lib/signup.txt lib/start.txt lib/text_message.txt
```

---

### **ثانياً: محتوى الملفات (بالتنسيق والمحتوى المحدث)**

الآن، انسخ المحتوى التالي والصقه في الملفات التي أنشأتها للتو.

#### `lib/config/env.dart`

```dart
// lib/config/env.dart

class Env {
  // عنوان URL الأساسي للـ API الخاص بك
  // تأكد من أن هذا هو الرابط الصحيح الذي تستخدمه للوصول إلى واجهة برمجة التطبيقات (API)
  static const String baseUrl = 'https://bisque-bear-644012.hostingersite.com/api';

  // عنوان URL الأساسي لملفات التخزين (مثل الصور والمستندات)
  static const String storageBaseUrl = 'https://bisque-bear-644012.hostingersite.com/storage';

  // يمكنك إضافة متغيرات بيئة أخرى هنا
  // static const String apiKey = 'YOUR_API_KEY_IF_NEEDED';
}

```

#### `lib/models/admin_model.dart`

```dart
// lib/models/admin_model.dart

class Admin {
  final int adminId;
  final int userId;
  final String fullName;
  final String? contactEmail;
  final String? contactPhone;
  final String? createdAt;
  final String? updatedAt;

  Admin({
    required this.adminId,
    required this.userId,
    required this.fullName,
    this.contactEmail,
    this.contactPhone,
    this.createdAt,
    this.updatedAt,
  });

  factory Admin.fromJson(Map<String, dynamic> json) {
    return Admin(
      adminId: json['admin_id'] as int,
      userId: json['user_id'] as int,
      fullName: json['full_name'] as String,
      contactEmail: json['contact_email'] as String?,
      contactPhone: json['contact_phone'] as String?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'admin_id': adminId,
      'user_id': userId,
      'full_name': fullName,
      'contact_email': contactEmail,
      'contact_phone': contactPhone,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/kindergarten_class_model.dart`

```dart
// lib/models/kindergarten_class_model.dart

// ملاحظة: Circular dependency محتملة مع Child و User.
// في هذه الحالة، يجب تمرير البيانات أو فصلها، لكن لغرض النموذج،
// سنفترض عدم وجود علاقات معكوسة مباشرة مدمجة هنا لتجنب التعقيد.

class KindergartenClass {
  final int classId;
  final String className;
  final String? description;
  final int? minAge;
  final int? maxAge;
  final String? createdAt;
  final String? updatedAt;

  KindergartenClass({
    required this.classId,
    required this.className,
    this.description,
    this.minAge,
    this.maxAge,
    this.createdAt,
    this.updatedAt,
  });

  String get ageRange {
    if (minAge != null && maxAge != null) {
      return '$minAge - $maxAge سنوات';
    } else if (minAge != null) {
      return 'أكثر من $minAge سنوات';
    } else if (maxAge != null) {
      return 'حتى $maxAge سنوات';
    }
    return 'غير محدد';
  }

  factory KindergartenClass.fromJson(Map<String, dynamic> json) {
    return KindergartenClass(
      classId: json['class_id'] as int,
      className: json['class_name'] as String,
      description: json['description'] as String?,
      minAge: json['min_age'] as int?,
      maxAge: json['max_age'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'class_id': classId,
      'class_name': className,
      'description': description,
      'min_age': minAge,
      'max_age': maxAge,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/educational_resource_model.dart`

```dart
// lib/models/educational_resource_model.dart

import '../config/env.dart';
import 'admin_model.dart'; // النموذج الذي أنشأناه

class EducationalResource {
  final int resourceId;
  final String title;
  final String? description;
  final String resourceType;
  final String urlOrPath;
  final int? targetAgeMin;
  final int? targetAgeMax;
  final String? subject;
  final int addedById;
  final String? createdAt;
  final String? updatedAt;

  final Admin? addedBy; // تم تغيير addedByAdmin إلى addedBy ليتطابق مع الرد الفعلي

  EducationalResource({
    required this.resourceId,
    required this.title,
    this.description,
    required this.resourceType,
    required this.urlOrPath,
    this.targetAgeMin,
    this.targetAgeMax,
    this.subject,
    required this.addedById,
    this.createdAt,
    this.updatedAt,
    this.addedBy,
  });

  String get fullUrlOrPath {
    if (urlOrPath.startsWith('http://') || urlOrPath.startsWith('https://')) {
      return urlOrPath;
    }
    return '${Env.storageBaseUrl}/$urlOrPath';
  }

  String translatedResourceType() {
    switch (resourceType.toLowerCase()) {
      case 'video':
        return 'فيديو';
      case 'pdf':
        return 'ملف PDF';
      case 'article':
        return 'مقالة';
      case 'interactive_game':
        return 'لعبة تفاعلية';
      case 'image':
        return 'صورة';
      case 'link':
        return 'رابط خارجي';
      default:
        return resourceType;
    }
  }

  factory EducationalResource.fromJson(Map<String, dynamic> json) {
    return EducationalResource(
      resourceId: json['resource_id'] as int,
      title: json['title'] as String,
      description: json['description'] as String?,
      resourceType: json['resource_type'] as String,
      urlOrPath: json['url_or_path'] as String,
      targetAgeMin: json['target_age_min'] as int?,
      targetAgeMax: json['target_age_max'] as int?,
      subject: json['subject'] as String?,
      addedById: json['added_by_id'] as int,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      addedBy: json['added_by'] != null // تم تغيير اسم العلاقة هنا
          ? Admin.fromJson(json['added_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'resource_id': resourceId,
      'title': title,
      'description': description,
      'resource_type': resourceType,
      'url_or_path': urlOrPath,
      'target_age_min': targetAgeMin,
      'target_age_max': targetAgeMax,
      'subject': subject,
      'added_by_id': addedById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/parent_model.dart`

```dart
// lib/models/parent_model.dart

// ملاحظة: تم حذف استيراد user_model و child_model و observation_model هنا لتجنب circular dependency
// في معظم الحالات، تكون الكائنات الرئيسية فقط مطلوبة عند إنشاء النموذج الأساسي،
// بينما يتم "تضمين" العلاقات عند طلبها من الـ API (مع `with` أو `load`).
// إذا كنت بحاجة لـ `User` أو `Child` أو `Observation` داخل `ParentModel` (والعكس صحيح)،
// ستحتاج إلى حل مثل استخدام كائنات بسيطة ID-only أو فصل الفارسرات/الجالبة.

class ParentModel {
  final int parentId;
  final int userId;
  final String fullName;
  final String contactEmail;
  final String contactPhone;
  final String? address;
  final String? createdAt;
  final String? updatedAt;

  ParentModel({
    required this.parentId,
    required this.userId,
    required this.fullName,
    required this.contactEmail,
    required this.contactPhone,
    this.address,
    this.createdAt,
    this.updatedAt,
  });

  factory ParentModel.fromJson(Map<String, dynamic> json) {
    return ParentModel(
      parentId: json['parent_id'] as int,
      userId: json['user_id'] as int,
      fullName: json['full_name'] as String,
      contactEmail: json['contact_email'] as String,
      contactPhone: json['contact_phone'] as String,
      address: json['address'] as String?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'parent_id': parentId,
      'user_id': userId,
      'full_name': fullName,
      'contact_email': contactEmail,
      'contact_phone': contactPhone,
      'address': address,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/user_model.dart`

```dart
// lib/models/user_model.dart

import '../config/env.dart';
import 'admin_model.dart';
import 'parent_model.dart';
import 'kindergarten_class_model.dart'; // ستحتاج لتعريف هذا أو استيراده إذا كنت تدمجه

class User {
  final int id;
  final String name;
  final String email;
  final String role;
  final bool isActive;
  final String? emailVerifiedAt;
  final String? profilePictureUrl;
  final String? createdAt;
  final String? updatedAt;

  // العلاقات المضافة بناءً على نموذج Laravel المحدث
  final Admin? adminProfile;
  final ParentModel? parentProfile; // استخدام ParentModel
  final List<KindergartenClass>? supervisedClasses; // قائمة الكائنات
  // بناءً على الـ YAML، الـ `supervisor_profile` هو `AdminProfile` في Laravel (تم تسميته `Admin` هنا)
  final Admin? supervisorProfile; 

  User({
    required this.id,
    required this.name,
    required this.email,
    required this.role,
    required this.isActive,
    this.emailVerifiedAt,
    this.profilePictureUrl,
    this.createdAt,
    this.updatedAt,
    this.adminProfile,
    this.parentProfile,
    this.supervisedClasses,
    this.supervisorProfile,
  });

  String get displayName => name;

  String? get fullProfilePictureUrl {
    if (profilePictureUrl == null || profilePictureUrl!.isEmpty) {
      return null;
    }
    if (profilePictureUrl!.startsWith('http://') || profilePictureUrl!.startsWith('https://')) {
      return profilePictureUrl;
    }
    return '${Env.storageBaseUrl}/$profilePictureUrl';
  }

  String translatedRole() {
    switch (role.toLowerCase()) {
      case 'admin':
        return 'مدير النظام';
      case 'supervisor':
        return 'مشرف';
      case 'teacher':
        return 'معلم';
      case 'parent':
        return 'ولي أمر';
      default:
        return 'مستخدم (${role})';
    }
  }

  factory User.fromJson(Map<String, dynamic> json) {
    return User(
      id: json['id'] as int,
      name: json['name'] as String,
      email: json['email'] as String,
      role: json['role'] as String,
      isActive: json['is_active'] as bool,
      emailVerifiedAt: json['email_verified_at'] as String?,
      profilePictureUrl: json['profile_picture'] as String?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,

      // تحليل العلاقات المدمجة
      adminProfile: json['admin_profile'] != null
          ? Admin.fromJson(json['admin_profile'] as Map<String, dynamic>)
          : null,
      parentProfile: json['parent_profile'] != null
          ? ParentModel.fromJson(json['parent_profile'] as Map<String, dynamic>)
          : null,
      supervisedClasses: (json['supervised_classes'] as List<dynamic>?)
          ?.map((classJson) => KindergartenClass.fromJson(classJson as Map<String, dynamic>))
          .toList(),
      supervisorProfile: json['supervisor_profile'] != null // اسم العلاقة في Laravel هو supervisor_profile
          ? Admin.fromJson(json['supervisor_profile'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
      'email': email,
      'role': role,
      'is_active': isActive,
      'email_verified_at': emailVerifiedAt,
      'profile_picture': profilePictureUrl,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/announcement_model.dart` (محدثة)

```dart
// lib/models/announcement_model.dart

import 'admin_model.dart';
import 'kindergarten_class_model.dart'; // النموذج الذي أنشأناه

class Announcement {
  final int announcementId;
  final String title;
  final String content;
  final String publishDate;
  final int authorId;
  final int? targetClassId;
  final String? createdAt;
  final String? updatedAt;

  final Admin? author; // تم تغيير author من User إلى Admin بناءً على الرد
  final KindergartenClass? targetClass;

  Announcement({
    required this.announcementId,
    required this.title,
    required this.content,
    required this.publishDate,
    required this.authorId,
    this.targetClassId,
    this.createdAt,
    this.updatedAt,
    this.author,
    this.targetClass,
  });

  DateTime? get parsedPublishDate {
    try {
      return DateTime.parse(publishDate);
    } catch (e) {
      return null;
    }
  }

  factory Announcement.fromJson(Map<String, dynamic> json) {
    return Announcement(
      announcementId: json['announcement_id'] as int,
      title: json['title'] as String,
      content: json['content'] as String,
      publishDate: json['publish_date'] as String,
      authorId: json['author_id'] as int,
      targetClassId: json['target_class_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      author: json['author'] != null
          ? Admin.fromJson(json['author'] as Map<String, dynamic>)
          : null,
      targetClass: json['target_class'] != null
          ? KindergartenClass.fromJson(json['target_class'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'announcement_id': announcementId,
      'title': title,
      'content': content,
      'publish_date': publishDate,
      'author_id': authorId,
      'target_class_id': targetClassId,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/daily_meal_model.dart`

```dart
// lib/models/daily_meal_model.dart

import 'kindergarten_class_model.dart'; // النموذج الذي أنشأناه
// لا يمكن استيراد child_meal_status_model هنا بسبب Circular dependency

class DailyMeal {
  final int mealId;
  final String mealDate;
  final String mealType;
  final String menuDescription;
  final int? classId;
  final String? createdAt;
  final String? updatedAt;

  final KindergartenClass? kindergartenClass;

  DailyMeal({
    required this.mealId,
    required this.mealDate,
    required this.mealType,
    required this.menuDescription,
    this.classId,
    this.createdAt,
    this.updatedAt,
    this.kindergartenClass,
  });

  DateTime? get parsedMealDate {
    try {
      return DateTime.parse(mealDate);
    } catch (e) {
      return null;
    }
  }

  String translatedMealType() {
    switch (mealType.toLowerCase()) {
      case 'breakfast':
        return 'فطور';
      case 'lunch':
        return 'غداء';
      case 'snack':
        return 'وجبة خفيفة';
      default:
        return mealType;
    }
  }

  factory DailyMeal.fromJson(Map<String, dynamic> json) {
    return DailyMeal(
      mealId: json['meal_id'] as int,
      mealDate: json['meal_date'] as String,
      mealType: json['meal_type'] as String,
      menuDescription: json['menu_description'] as String,
      classId: json['class_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      kindergartenClass: json['kindergarten_class'] != null
          ? KindergartenClass.fromJson(json['kindergarten_class'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'meal_id': mealId,
      'meal_date': mealDate,
      'meal_type': mealType,
      'menu_description': menuDescription,
      'class_id': classId,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/child_meal_status_model.dart`

```dart
// lib/models/child_meal_status_model.dart

import 'child_model.dart'; // النموذج الذي أنشأناه
import 'daily_meal_model.dart'; // افترض وجود هذا النموذج
import 'user_model.dart'; // النموذج الذي أنشأناه

class ChildMealStatus {
  final int statusId;
  final int childId;
  final int mealId;
  final String consumptionStatus;
  final String? statusText; // تمت إضافته من الردود الفعلية
  final String? notes;
  final int? recordedById;
  final String? createdAt;
  final String? updatedAt;

  final Child? child;
  final DailyMeal? meal; // تم تغيير الاسم من dailyMeal إلى meal
  final User? recordedBy;

  ChildMealStatus({
    required this.statusId,
    required this.childId,
    required this.mealId,
    required this.consumptionStatus,
    this.statusText,
    this.notes,
    this.recordedById,
    this.createdAt,
    this.updatedAt,
    this.child,
    this.meal,
    this.recordedBy,
  });

  factory ChildMealStatus.fromJson(Map<String, dynamic> json) {
    return ChildMealStatus(
      statusId: json['status_id'] as int,
      childId: json['child_id'] as int,
      mealId: json['meal_id'] as int,
      consumptionStatus: json['consumption_status'] as String,
      statusText: json['status_text'] as String?, // تمت إضافته
      notes: json['notes'] as String?,
      recordedById: json['recorded_by_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      child: json['child'] != null
          ? Child.fromJson(json['child'] as Map<String, dynamic>)
          : null,
      meal: json['meal'] != null // تم تغيير اسم المفتاح هنا
          ? DailyMeal.fromJson(json['meal'] as Map<String, dynamic>)
          : null,
      recordedBy: json['recorded_by'] != null
          ? User.fromJson(json['recorded_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'status_id': statusId,
      'child_id': childId,
      'meal_id': mealId,
      'consumption_status': consumptionStatus,
      'status_text': statusText,
      'notes': notes,
      'recorded_by_id': recordedById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/weekly_schedule_model.dart`

```dart
// lib/models/weekly_schedule_model.dart

import 'kindergarten_class_model.dart'; // النموذج الذي أنشأناه
import 'user_model.dart'; // النموذج الذي أنشأناه

class WeeklySchedule {
  final int scheduleId;
  final int classId;
  final String dayOfWeek;
  final String startTime;
  final String endTime;
  final String activityDescription;
  final int? createdById;
  final String? createdAt;
  final String? updatedAt;

  final KindergartenClass? kindergartenClass; // تم تغيير الاسم ليتوافق
  final User? createdBy; // تم تغيير createdByAdmin إلى createdBy و نوعه User

  WeeklySchedule({
    required this.scheduleId,
    required this.classId,
    required this.dayOfWeek,
    required this.startTime,
    required this.endTime,
    required this.activityDescription,
    this.createdById,
    this.createdAt,
    this.updatedAt,
    this.kindergartenClass,
    this.createdBy,
  });

  String translatedDayOfWeek() {
    switch (dayOfWeek.toLowerCase()) {
      case 'monday':
        return 'الاثنين';
      case 'tuesday':
        return 'الثلاثاء';
      case 'wednesday':
        return 'الأربعاء';
      case 'thursday':
        return 'الخميس';
      case 'friday':
        return 'الجمعة';
      case 'saturday':
        return 'السبت';
      case 'sunday':
        return 'الأحد';
      default:
        return dayOfWeek;
    }
  }

  factory WeeklySchedule.fromJson(Map<String, dynamic> json) {
    return WeeklySchedule(
      scheduleId: json['schedule_id'] as int,
      classId: json['class_id'] as int,
      dayOfWeek: json['day_of_week'] as String,
      startTime: json['start_time'] as String,
      endTime: json['end_time'] as String,
      activityDescription: json['activity_description'] as String,
      createdById: json['created_by_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      kindergartenClass: json['kindergarten_class'] != null
          ? KindergartenClass.fromJson(json['kindergarten_class'] as Map<String, dynamic>)
          : null,
      createdBy: json['created_by'] != null // اسم العلاقة في الرد هو created_by
          ? User.fromJson(json['created_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'schedule_id': scheduleId,
      'class_id': classId,
      'day_of_week': dayOfWeek,
      'start_time': startTime,
      'end_time': endTime,
      'activity_description': activityDescription,
      'created_by_id': createdById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/attendance_model.dart`

```dart
// lib/models/attendance_model.dart

import 'child_model.dart';
import 'user_model.dart';

class Attendance {
  final int attendanceId;
  final int childId;
  final String attendanceDate;
  final String status;
  final String? checkInTime;
  final String? checkOutTime;
  final String? notes;
  final int recordedById;
  final String? createdAt;
  final String? updatedAt;

  final Child? child;
  final User? recordedBy; // تم تغيير الاسم إلى recordedBy

  Attendance({
    required this.attendanceId,
    required this.childId,
    required this.attendanceDate,
    required this.status,
    this.checkInTime,
    this.checkOutTime,
    this.notes,
    required this.recordedById,
    this.createdAt,
    this.updatedAt,
    this.child,
    this.recordedBy,
  });

  DateTime? get parsedAttendanceDate {
    try {
      return DateTime.parse(attendanceDate);
    } catch (e) {
      return null;
    }
  }

  factory Attendance.fromJson(Map<String, dynamic> json) {
    return Attendance(
      attendanceId: json['attendance_id'] as int,
      childId: json['child_id'] as int,
      attendanceDate: json['attendance_date'] as String,
      status: json['status'] as String,
      checkInTime: json['check_in_time'] as String?,
      checkOutTime: json['check_out_time'] as String?,
      notes: json['notes'] as String?,
      recordedById: json['recorded_by_id'] as int,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      child: json['child'] != null
          ? Child.fromJson(json['child'] as Map<String, dynamic>)
          : null,
      recordedBy: json['recorded_by'] != null // اسم العلاقة في الرد
          ? User.fromJson(json['recorded_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'attendance_id': attendanceId,
      'child_id': childId,
      'attendance_date': attendanceDate,
      'status': status,
      'check_in_time': checkInTime,
      'check_out_time': checkOutTime,
      'notes': notes,
      'recorded_by_id': recordedById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/health_record_model.dart`

```dart
// lib/models/health_record_model.dart

import '../config/env.dart';
import 'child_model.dart';
import 'user_model.dart';

class HealthRecord {
  final int recordId;
  final int childId;
  final String recordType;
  final String recordDate;
  final String? details;
  final String? nextDueDate;
  final String? documentPath;
  final int? enteredById;
  final String? createdAt;
  final String? updatedAt;

  final Child? child;
  final User? enteredBy; // تم تغيير الاسم إلى enteredBy

  HealthRecord({
    required this.recordId,
    required this.childId,
    required this.recordType,
    required this.recordDate,
    this.details,
    this.nextDueDate,
    this.documentPath,
    this.enteredById,
    this.createdAt,
    this.updatedAt,
    this.child,
    this.enteredBy,
  });

  DateTime? get parsedRecordDate {
    try {
      return DateTime.parse(recordDate);
    } catch (e) {
      return null;
    }
  }

  DateTime? get parsedNextDueDate {
    if (nextDueDate == null) return null;
    try {
      return DateTime.parse(nextDueDate!);
    } catch (e) {
      return null;
    }
  }

  String? get fullDocumentUrl {
    if (documentPath == null || documentPath!.isEmpty) {
      return null;
    }
    if (documentPath!.startsWith('http://') || documentPath!.startsWith('https://')) {
      return documentPath;
    }
    return '${Env.storageBaseUrl}/$documentPath';
  }

  String translatedRecordType() {
    switch (recordType.toLowerCase()) {
      case 'vaccination':
        return 'تطعيم';
      case 'checkup':
        return 'فحص طبي';
      case 'illness': // من الرد
        return 'مرض';
      case 'medicationadministered': // من الرد
        return 'دواء مُعطى';
      default:
        return recordType;
    }
  }

  factory HealthRecord.fromJson(Map<String, dynamic> json) {
    return HealthRecord(
      recordId: json['record_id'] as int,
      childId: json['child_id'] as int,
      recordType: json['record_type'] as String,
      recordDate: json['record_date'] as String,
      details: json['details'] as String?,
      nextDueDate: json['next_due_date'] as String?,
      documentPath: json['document_path'] as String?,
      enteredById: json['entered_by_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      child: json['child'] != null
          ? Child.fromJson(json['child'] as Map<String, dynamic>)
          : null,
      enteredBy: json['entered_by'] != null // اسم العلاقة في الرد
          ? User.fromJson(json['entered_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'record_id': recordId,
      'child_id': childId,
      'record_type': recordType,
      'record_date': recordDate,
      'details': details,
      'next_due_date': nextDueDate,
      'document_path': documentPath,
      'entered_by_id': enteredById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/observation_model.dart`

```dart
// lib/models/observation_model.dart

import 'parent_model.dart';
import 'child_model.dart';

class Observation {
  final int observationId;
  final int parentId;
  final int? childId; // يمكن أن يكون null
  final String observationText;
  final String submittedAt;
  final String? createdAt;
  final String? updatedAt;

  final ParentModel? parentSubmitter;
  final Child? child;

  Observation({
    required this.observationId,
    required this.parentId,
    this.childId,
    required this.observationText,
    required this.submittedAt,
    this.createdAt,
    this.updatedAt,
    this.parentSubmitter,
    this.child,
  });

  DateTime? get parsedSubmittedAt {
    try {
      return DateTime.parse(submittedAt);
    } catch (e) {
      return null;
    }
  }

  factory Observation.fromJson(Map<String, dynamic> json) {
    return Observation(
      observationId: json['observation_id'] as int,
      parentId: json['parent_id'] as int,
      childId: json['child_id'] as int?,
      observationText: json['observation_text'] as String,
      submittedAt: json['submitted_at'] as String,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      parentSubmitter: json['parent_submitter'] != null
          ? ParentModel.fromJson(json['parent_submitter'] as Map<String, dynamic>)
          : null,
      child: json['child'] != null
          ? Child.fromJson(json['child'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'observation_id': observationId,
      'parent_id': parentId,
      'child_id': childId,
      'observation_text': observationText,
      'submitted_at': submittedAt,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/child_model.dart` (محدثة)

```dart
// lib/models/child_model.dart

import '../config/env.dart';
import 'kindergarten_class_model.dart';
import 'parent_model.dart';
import 'health_record_model.dart';
import 'attendance_model.dart';
import 'child_meal_status_model.dart'; // افترض وجود هذا النموذج
import 'event_registration_model.dart'; // لا توجد في ردودك، لكن للحفاظ على الأصل
import 'media_model.dart'; // لا توجد في ردودك، لكن للحفاظ على الأصل
import 'observation_model.dart'; // لا توجد في ردودك، لكن للحفاظ على الأصل

class Child {
  final int childId;
  final String firstName;
  final String lastName;
  // تم إزالة fullName من الخصائص المباشرة لأنه لا يظهر في الرد
  final String dateOfBirth;
  final String gender;
  final String enrollmentDate;
  final int? classId;
  final String? allergies;
  final String? medicalNotes;
  final String? photoUrl;
  final String? createdAt;
  final String? updatedAt;
  final Map<String, dynamic>? pivot; // تمت إضافته بناءً على رد /api/children

  // علاقات مدمجة
  final KindergartenClass? kindergartenClass; // تم تغيير الاسم
  final List<ParentModel>? parents; // لا تظهر في ردودك
  final List<HealthRecord>? healthRecords;
  final List<Attendance>? attendances; // تمت إضافتها
  final List<EventRegistration>? eventRegistrations; // لا تظهر في ردودك
  final List<Media>? media; // لا تظهر في ردودك
  final List<Observation>? observations; // لا تظهر في ردودك
  final List<ChildMealStatus>? mealStatuses; // لا تظهر في ردودك

  Child({
    required this.childId,
    required this.firstName,
    required this.lastName,
    required this.dateOfBirth,
    required this.gender,
    required this.enrollmentDate,
    this.classId,
    this.allergies,
    this.medicalNotes,
    this.photoUrl,
    this.createdAt,
    this.updatedAt,
    this.pivot,
    // علاقات اختيارية
    this.kindergartenClass,
    this.parents,
    this.healthRecords,
    this.attendances,
    this.eventRegistrations,
    this.media,
    this.observations,
    this.mealStatuses,
  });

  // دالة مساعدة للحصول على الاسم الكامل
  String get fullCalculatedName => '$firstName $lastName';

  String? get fullPhotoUrl {
    if (photoUrl == null || photoUrl!.isEmpty) {
      return null;
    }
    if (photoUrl!.startsWith('http://') || photoUrl!.startsWith('https://')) {
      return photoUrl;
    }
    return '${Env.storageBaseUrl}/$photoUrl';
  }

  DateTime? get parsedDateOfBirth {
    try {
      return DateTime.parse(dateOfBirth);
    } catch (e) {
      return null;
    }
  }

  DateTime? get parsedEnrollmentDate {
    try {
      return DateTime.parse(enrollmentDate);
    } catch (e) {
      return null;
    }
  }

  factory Child.fromJson(Map<String, dynamic> json) {
    return Child(
      childId: json['child_id'] as int,
      firstName: json['first_name'] as String,
      lastName: json['last_name'] as String,
      dateOfBirth: json['date_of_birth'] as String,
      gender: json['gender'] as String,
      enrollmentDate: json['enrollment_date'] as String,
      classId: json['class_id'] as int?,
      allergies: json['allergies'] as String?,
      medicalNotes: json['medical_notes'] as String?,
      photoUrl: json['photo_url'] as String?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      pivot: json['pivot'] as Map<String, dynamic>?, // تمت إضافته

      kindergartenClass: json['kindergarten_class'] != null
          ? KindergartenClass.fromJson(json['kindergarten_class'] as Map<String, dynamic>)
          : null,
      healthRecords: (json['health_records'] as List<dynamic>?)
          ?.map((recordJson) => HealthRecord.fromJson(recordJson as Map<String, dynamic>))
          .toList(),
      attendances: (json['attendances'] as List<dynamic>?)
          ?.map((attJson) => Attendance.fromJson(attJson as Map<String, dynamic>))
          .toList(),
      // الحقول التي لم تظهر في الردود لكن تم الحفاظ عليها من التوثيق الأولي
      parents: (json['parents'] as List<dynamic>?)
          ?.map((parentJson) => ParentModel.fromJson(parentJson as Map<String, dynamic>))
          .toList(),
      eventRegistrations: (json['event_registrations'] as List<dynamic>?)
          ?.map((regJson) => EventRegistration.fromJson(regJson as Map<String, dynamic>))
          .toList(),
      media: (json['media'] as List<dynamic>?)
          ?.map((mediaJson) => Media.fromJson(mediaJson as Map<String, dynamic>))
          .toList(),
      observations: (json['observations'] as List<dynamic>?)
          ?.map((obsJson) => Observation.fromJson(obsJson as Map<String, dynamic>))
          .toList(),
      mealStatuses: (json['meal_statuses'] as List<dynamic>?)
          ?.map((mealJson) => ChildMealStatus.fromJson(mealJson as Map<String, dynamic>))
          .toList(),
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'child_id': childId,
      'first_name': firstName,
      'last_name': lastName,
      'date_of_birth': dateOfBirth,
      'gender': gender,
      'enrollment_date': enrollmentDate,
      'class_id': classId,
      'allergies': allergies,
      'medical_notes': medicalNotes,
      'photo_url': photoUrl,
      'created_at': createdAt,
      'updated_at': updatedAt,
      'pivot': pivot, // تضمين Pivot إذا كانت تُرسل
    };
  }
}
```

#### `lib/models/event_model.dart`

```dart
// lib/models/event_model.dart

import 'admin_model.dart';
// EventRegistration و Child و Media يتم استيرادها في الفارسرات لتجنب circular dependency
// هنا سنستخدم List<dynamic> ثم نتحقق من النوع.

class Event {
  final int eventId;
  final String eventName;
  final String? description;
  final String eventDate;
  final String? location;
  final bool requiresRegistration;
  final String? registrationDeadline;
  final int createdById;
  final String? createdAt;
  final String? updatedAt;

  final Admin? createdBy; // تم تغيير createdByAdmin إلى createdBy
  // تم إزالة registrations, children, media مباشرة هنا لتجنب circular dependency.
  // سيتم تحليلها مباشرة في Factory من JSON.

  Event({
    required this.eventId,
    required this.eventName,
    this.description,
    required this.eventDate,
    this.location,
    required this.requiresRegistration,
    this.registrationDeadline,
    required this.createdById,
    this.createdAt,
    this.updatedAt,
    this.createdBy,
  });

  DateTime? get parsedEventDate {
    try {
      return DateTime.parse(eventDate);
    } catch (e) {
      return null;
    }
  }

  DateTime? get parsedRegistrationDeadline {
    if (registrationDeadline == null) return null;
    try {
      return DateTime.parse(registrationDeadline!);
    } catch (e) {
      return null;
    }
  }

  factory Event.fromJson(Map<String, dynamic> json) {
    // يمكن هنا استدعاء fromJson للنماذج الأخرى بشكل مباشر إذا تم حل مشاكل Circular import
    // وإلا، يتم التعامل معها كـ Map<String, dynamic> أو تجاهلها مؤقتاً
    return Event(
      eventId: json['event_id'] as int,
      eventName: json['event_name'] as String,
      description: json['description'] as String?,
      eventDate: json['event_date'] as String,
      location: json['location'] as String?,
      requiresRegistration: json['requires_registration'] as bool,
      registrationDeadline: json['registration_deadline'] as String?,
      createdById: json['created_by_id'] as int,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      createdBy: json['created_by'] != null // اسم العلاقة في الرد
          ? Admin.fromJson(json['created_by'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'event_id': eventId,
      'event_name': eventName,
      'description': description,
      'event_date': eventDate,
      'location': location,
      'requires_registration': requiresRegistration,
      'registration_deadline': registrationDeadline,
      'created_by_id': createdById,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/event_registration_model.dart`

```dart
// lib/models/event_registration_model.dart

// ملاحظة: Circular dependency محتملة مع Event و Child.
// هنا سنبسطها بحيث لا تحتوي على الكائنات المدمجة بشكل افتراضي لتجنب المشاكل
// ولكنها ستقبلها من الـ API إذا تم تحميلها (من خلال json['event'] مثلاً).
// لتجنب الاستيراد المتبادل، قد تحتاج إلى تمرير البيانات بدلاً من كائن كامل.

import 'event_model.dart';
import 'child_model.dart';

class EventRegistration {
  final int registrationId;
  final int eventId;
  final int childId;
  final String registrationDate;
  final bool parentConsent;
  final String? createdAt;
  final String? updatedAt;

  // الحقول المتعلقة بالعلاقات يمكن أن تكون Map أو نوع خاص
  final Event? event;
  final Child? child;

  EventRegistration({
    required this.registrationId,
    required this.eventId,
    required this.childId,
    required this.registrationDate,
    required this.parentConsent,
    this.createdAt,
    this.updatedAt,
    this.event,
    this.child,
  });

  DateTime? get parsedRegistrationDate {
    try {
      return DateTime.parse(registrationDate);
    } catch (e) {
      return null;
    }
  }

  factory EventRegistration.fromJson(Map<String, dynamic> json) {
    return EventRegistration(
      registrationId: json['registration_id'] as int,
      eventId: json['event_id'] as int,
      childId: json['child_id'] as int,
      registrationDate: json['registration_date'] as String,
      parentConsent: json['parent_consent'] as bool,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      // يمكنك محاولة تحليل العلاقات هنا إذا تم تجنب Circular dependency
      event: json['event'] != null && json['event'] is Map<String, dynamic>
          ? Event.fromJson(json['event'] as Map<String, dynamic>)
          : null,
      child: json['child'] != null && json['child'] is Map<String, dynamic>
          ? Child.fromJson(json['child'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'registration_id': registrationId,
      'event_id': eventId,
      'child_id': childId,
      'registration_date': registrationDate,
      'parent_consent': parentConsent,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/media_model.dart`

```dart
// lib/models/media_model.dart

import '../config/env.dart';
// لنفترض أننا لا ندمج كائنات كاملة لتجنب circular dependencies هنا.
// User و Child و Event و KindergartenClass قد تتسبب في مشاكل استيراد.
// سنسكتفي بـ ID ونتعامل معها في الـ UI عند الحاجة لجلب التفاصيل.
// إذا كنت بحاجة لدمجها، تأكد من ترتيب ملفات الموديل بشكل صحيح.

class Media {
  final int mediaId;
  final String filePath;
  final String mediaType;
  final String? description;
  final String uploadDate;
  final int? uploaderId;
  final int? associatedChildId;
  final int? associatedEventId;
  final int? associatedClassId;
  final String? createdAt;
  final String? updatedAt;

  // الحقول التي تمثل الكائنات المدمجة، لكن هنا سنحافظ عليها كـ IDs فقط أو نNull
  // final User? uploader;
  // final Child? associatedChild;
  // final Event? associatedEvent;
  // final KindergartenClass? associatedClass;

  Media({
    required this.mediaId,
    required this.filePath,
    required this.mediaType,
    this.description,
    required this.uploadDate,
    this.uploaderId,
    this.associatedChildId,
    this.associatedEventId,
    this.associatedClassId,
    this.createdAt,
    this.updatedAt,
    // this.uploader,
    // this.associatedChild,
    // this.associatedEvent,
    // this.associatedClass,
  });

  String get fullFilePath {
    if (filePath.startsWith('http://') || filePath.startsWith('https://')) {
      return filePath;
    }
    return '${Env.storageBaseUrl}/$filePath';
  }

  DateTime? get parsedUploadDate {
    try {
      return DateTime.parse(uploadDate);
    } catch (e) {
      return null;
    }
  }

  String translatedMediaType() {
    switch (mediaType.toLowerCase()) {
      case 'image':
        return 'صورة';
      case 'video':
        return 'فيديو';
      case 'document':
        return 'مستند';
      case 'audio':
        return 'صوت';
      default:
        return mediaType;
    }
  }

  factory Media.fromJson(Map<String, dynamic> json) {
    return Media(
      mediaId: json['media_id'] as int,
      filePath: json['file_path'] as String,
      mediaType: json['media_type'] as String,
      description: json['description'] as String?,
      uploadDate: json['upload_date'] as String,
      uploaderId: json['uploader_id'] as int?,
      associatedChildId: json['associated_child_id'] as int?,
      associatedEventId: json['associated_event_id'] as int?,
      associatedClassId: json['associated_class_id'] as int?,
      createdAt: json['created_at'] as String?,
      updatedAt: json['updated_at'] as String?,
      // هنا يمكنك تحليل الكائنات إذا لم تكن هناك circular dependencies
      // uploader: json['uploader'] != null ? User.fromJson(json['uploader'] as Map<String, dynamic>) : null,
      // associatedChild: json['associated_child'] != null ? Child.fromJson(json['associated_child'] as Map<String, dynamic>) : null,
      // associatedEvent: json['associated_event'] != null ? Event.fromJson(json['associated_event'] as Map<String, dynamic>) : null,
      // associatedClass: json['associated_class'] != null ? KindergartenClass.fromJson(json['associated_class'] as Map<String, dynamic>) : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'media_id': mediaId,
      'file_path': filePath,
      'media_type': mediaType,
      'description': description,
      'upload_date': uploadDate,
      'uploader_id': uploaderId,
      'associated_child_id': associatedChildId,
      'associated_event_id': associatedEventId,
      'associated_class_id': associatedClassId,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/models/message_model.dart`

```dart
// lib/models/message_model.dart

import 'user_model.dart';

class Message {
  final int messageId;
  final int senderId;
  final int recipientId;
  final String? subject;
  final String body;
  final String sentAt;
  final String? readAt;
  final String? createdAt; // تمت إضافتها بناءً على الردود
  final String? updatedAt; // تمت إضافتها بناءً على الردود

  final User? sender;
  final User? recipient;

  Message({
    required this.messageId,
    required this.senderId,
    required this.recipientId,
    this.subject,
    required this.body,
    required this.sentAt,
    this.readAt,
    this.createdAt,
    this.updatedAt,
    this.sender,
    this.recipient,
  });

  DateTime? get parsedSentAt {
    try {
      return DateTime.parse(sentAt);
    } catch (e) {
      return null;
    }
  }

  DateTime? get parsedReadAt {
    if (readAt == null) return null;
    try {
      return DateTime.parse(readAt!);
    } catch (e) {
      return null;
    }
  }

  bool get isRead => readAt != null;

  factory Message.fromJson(Map<String, dynamic> json) {
    return Message(
      messageId: json['message_id'] as int,
      senderId: json['sender_id'] as int,
      recipientId: json['recipient_id'] as int,
      subject: json['subject'] as String?,
      body: json['body'] as String,
      sentAt: json['sent_at'] as String,
      readAt: json['read_at'] as String?,
      createdAt: json['created_at'] as String?, // تمت إضافتها
      updatedAt: json['updated_at'] as String?, // تمت إضافتها
      sender: json['sender'] != null
          ? User.fromJson(json['sender'] as Map<String, dynamic>)
          : null,
      recipient: json['recipient'] != null
          ? User.fromJson(json['recipient'] as Map<String, dynamic>)
          : null,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'message_id': messageId,
      'sender_id': senderId,
      'recipient_id': recipientId,
      'subject': subject,
      'body': body,
      'sent_at': sentAt,
      'read_at': readAt,
      'created_at': createdAt,
      'updated_at': updatedAt,
    };
  }
}
```

#### `lib/providers/auth/auth_provider.dart` (جاهز للتوسيع)

```dart
// lib/providers/auth/auth_provider.dart

import 'package:flutter/material.dart';
// import 'package:kids/models/user_model.dart'; // ستحتاج لنموذج المستخدم
// import 'package:http/http.dart' as http; // للتعامل مع طلبات HTTP
// import 'dart:convert';
// import 'package:kids/config/env.dart'; // لاستخدام الـ Base URL

class AuthProvider with ChangeNotifier {
  // User? _user;
  // String? _token;

  // User? get user => _user;
  // String? get token => _token;
  // bool get isAuthenticated => _user != null && _token != null;

  // AuthProvider() {
  //   // حاول تحميل التوكن من Shared Preferences عند بدء التطبيق
  //   _loadUserAndToken();
  // }

  // Future<void> _loadUserAndToken() async {
  //   // استخدم shared_preferences لحفظ/جلب التوكن وبيانات المستخدم
  // }

  // Future<void> login(String email, String password, String deviceName) async {
  //   // منطق طلب تسجيل الدخول إلى الـ API
  //   // final response = await http.post(
  //   //   Uri.parse('${Env.baseUrl}/login'),
  //   //   headers: {'Content-Type': 'application/json'},
  //   //   body: json.encode({
  //   //     'email': email,
  //   //     'password': password,
  //   //     'device_name': deviceName,
  //   //   }),
  //   // );

  //   // إذا كانت استجابة ناجحة
  //   // _user = User.fromJson(jsonDecode(response.body)['user']);
  //   // _token = jsonDecode(response.body)['token'];
  //   // حفظ التوكن وبيانات المستخدم في Shared Preferences
  //   // notifyListeners();
  // }

  // Future<void> logout() async {
  //   // منطق طلب تسجيل الخروج إلى الـ API
  //   // ثم حذف التوكن وبيانات المستخدم من Shared Preferences
  //   // _user = null;
  //   // _token = null;
  //   // notifyListeners();
  // }
}
```

#### `lib/providers/children/children_provider.dart` (جاهز للتوسيع)

```dart
// lib/providers/children/children_provider.dart

import 'package:flutter/material.dart';
// import 'package:kids/models/child_model.dart';
// import 'package:http/http.dart' as http;
// import 'dart:convert';
// import 'package:kids/config/env.dart';

class ChildrenProvider with ChangeNotifier {
  // List<Child> _children = [];
  // bool _isLoading = false;

  // List<Child> get children => _children;
  // bool get isLoading => _isLoading;

  // Future<void> fetchChildren(String token) async {
  //   // _isLoading = true;
  //   // notifyListeners();

  //   // final response = await http.get(
  //   //   Uri.parse('${Env.baseUrl}/children'),
  //   //   headers: {
  //   //     'Content-Type': 'application/json',
  //   //     'Authorization': 'Bearer $token',
  //   //   },
  //   // );

  //   // if (response.statusCode == 200) {
  //   //   final List<dynamic> childrenJson = json.decode(response.body)['data'];
  //   //   _children = childrenJson.map((json) => Child.fromJson(json)).toList();
  //   // } else {
  //   //   // التعامل مع الأخطاء
  //   //   print('Failed to load children: ${response.statusCode}');
  //   // }

  //   // _isLoading = false;
  //   // notifyListeners();
  // }

  // Future<Child?> fetchChildDetails(int childId, String token) async {
  //   // // منطق جلب تفاصيل طفل محدد
  //   // final response = await http.get(
  //   //   Uri.parse('${Env.baseUrl}/children/$childId'),
  //   //   headers: {
  //   //     'Content-Type': 'application/json',
  //   //     'Authorization': 'Bearer $token',
  //   //   },
  //   // );

  //   // if (response.statusCode == 200) {
  //   //   return Child.fromJson(json.decode(response.body)['data']);
  //   // } else {
  //   //   print('Failed to load child details: ${response.statusCode}');
  //   //   return null;
  //   // }
  // }
}
```

#### `lib/providers/home_data/home_data_provider.dart` (جاهز للتوسيع)

```dart
// lib/providers/home_data/home_data_provider.dart

import 'package:flutter/material.dart';
// import 'package:kids/models/announcement_model.dart';
// import 'package:kids/models/weekly_schedule_model.dart';
// import 'package:kids/models/media_model.dart';
// import 'package:http/http.dart' as http;
// import 'dart:convert';
// import 'package:kids/config/env.dart';

class HomeDataProvider with ChangeNotifier {
  // List<Announcement> _announcements = [];
  // List<WeeklySchedule> _weeklySchedules = [];
  // List<Media> _mediaItems = [];
  // bool _isLoading = false;

  // List<Announcement> get announcements => _announcements;
  // List<WeeklySchedule> get weeklySchedules => _weeklySchedules;
  // List<Media> get mediaItems => _mediaItems;
  // bool get isLoading => _isLoading;

  // Future<void> fetchHomeData(String token) async {
  //   // _isLoading = true;
  //   // notifyListeners();

  //   // try {
  //   //   // جلب الإعلانات
  //   //   final announcementsResponse = await http.get(
  //   //     Uri.parse('${Env.baseUrl}/announcements'),
  //   //     headers: {'Authorization': 'Bearer $token'},
  //   //   );
  //   //   if (announcementsResponse.statusCode == 200) {
  //   //     _announcements = (json.decode(announcementsResponse.body)['data'] as List)
  //   //         .map((item) => Announcement.fromJson(item))
  //   //         .toList();
  //   //   }

  //   //   // جلب الجداول
  //   //   final schedulesResponse = await http.get(
  //   //     Uri.parse('${Env.baseUrl}/schedules'),
  //   //     headers: {'Authorization': 'Bearer $token'},
  //   //   );
  //   //   if (schedulesResponse.statusCode == 200) {
  //   //     _weeklySchedules = (json.decode(schedulesResponse.body)['data'] as List)
  //   //         .map((item) => WeeklySchedule.fromJson(item))
  //   //         .toList();
  //   //   }

  //   //   // جلب الوسائط
  //   //   final mediaResponse = await http.get(
  //   //     Uri.parse('${Env.baseUrl}/media'),
  //   //     headers: {'Authorization': 'Bearer $token'},
  //   //   );
  //   //   if (mediaResponse.statusCode == 200) {
  //   //     _mediaItems = (json.decode(mediaResponse.body)['data'] as List)
  //   //         .map((item) => Media.fromJson(item))
  //   //         .toList();
  //   //   }

  //   // } catch (e) {
  //   //   print('Error fetching home data: $e');
  //   // }

  //   // _isLoading = false;
  //   // notifyListeners();
  // }
}
```

#### `lib/main.dart`

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:provider/provider.dart'; // لتفعيل Provider

import 'package:kids/start_app.dart';
import 'package:kids/providers/auth/auth_provider.dart';
import 'package:kids/providers/children/children_provider.dart';
import 'package:kids/providers/home_data/home_data_provider.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  SystemChrome.setPreferredOrientations([DeviceOrientation.portraitUp]);

  runApp(
    MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (context) => AuthProvider()),
        ChangeNotifierProvider(create: (context) => ChildrenProvider()),
        ChangeNotifierProvider(create: (context) => HomeDataProvider()),
        // أضف المزيد من الـ providers هنا حسب الحاجة
      ],
      child: MyApp(),
    ),
  );
}
```

#### `lib/start_app.dart`

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:flutter_staggered_animations/flutter_staggered_animations.dart'; // Keep if you use these elsewhere
import 'package:kids/screens/authentication/login_screen.dart'; // تم تغيير المسار
import 'package:kids/screens/main_sections/home_page.dart'; // تم تغيير المسار
import 'package:provider/provider.dart';
import 'package:kids/providers/auth/auth_provider.dart'; // لتفعيل Provider

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'روضة الأطفال العصرية',
      locale: const Locale('ar'),
      supportedLocales: const [
        Locale('ar', ''),
        Locale('en', ''),
      ],
      localizationsDelegates: const [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
        GlobalCupertinoLocalizations.delegate,
      ],
      theme: _buildAppTheme(),
      home: SplashScreen(),
      routes: {
        LoginScreen.routeName: (context) => LoginScreen(),
        HomePage.routeName: (context) => const HomePage(), // إضافة مسار الـ HomePage
      },
    );
  }

  ThemeData _buildAppTheme() {
    const primaryColor = Color.fromARGB(255, 236, 64, 122);
    const secondaryColor = Color.fromARGB(255, 171, 71, 188);
    const accentColor = Color.fromARGB(255, 129, 212, 250);
    const backgroundColor = Color(0xFFFFF8FD);
    const cardBackgroundColor = Colors.white;
    const errorColor = Color(0xFFD32F2F);

    final colorScheme = ColorScheme.fromSeed(
      seedColor: primaryColor,
      primary: primaryColor,
      secondary: secondaryColor,
      tertiary: accentColor,
      background: backgroundColor,
      surface: cardBackgroundColor,
      surfaceVariant: Colors.grey.shade100,
      onSurfaceVariant: Colors.grey.shade600,
      error: errorColor,
      brightness: Brightness.light,
      onPrimary: Colors.white,
      onSecondary: Colors.white,
      onBackground: Colors.black87,
      onSurface: Colors.black87,
      onError: Colors.white,
    );

    const textTheme = TextTheme(
      displayLarge: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: primaryColor,
        fontSize: 34,
      ),
      displayMedium: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: primaryColor,
        fontSize: 28,
      ),
      displaySmall: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: primaryColor,
        fontSize: 24,
      ),
      headlineLarge: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: secondaryColor,
        fontSize: 22,
      ),
      headlineMedium: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: Colors.white,
        fontSize: 20.0,
      ),
      headlineSmall: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: secondaryColor,
        fontSize: 18.0,
      ),
      titleLarge: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: Colors.black87,
        fontSize: 17.0,
      ),
      titleMedium: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.w600,
        color: Colors.black87,
        fontSize: 15.0,
      ),
      titleSmall: TextStyle(fontFamily: 'Cairo', color: Colors.black54),
      bodyLarge: TextStyle(
        fontFamily: 'Cairo',
        fontSize: 16.0,
        color: Colors.black87,
        height: 1.4,
      ),
      bodyMedium: TextStyle(
        fontFamily: 'Cairo',
        fontSize: 14.0,
        color: Colors.black54,
        height: 1.4,
      ),
      bodySmall: TextStyle(
        fontFamily: 'Cairo',
        fontSize: 12.0,
        color: Color.fromARGB(255, 153, 152, 152),
      ),
      labelLarge: TextStyle(
        fontFamily: 'Cairo',
        fontWeight: FontWeight.bold,
        color: Colors.white,
        fontSize: 16.0,
      ),
      labelMedium: TextStyle(fontFamily: 'Cairo', fontWeight: FontWeight.w600),
      labelSmall: TextStyle(fontFamily: 'Cairo', color: Colors.grey),
    );

    return ThemeData(
      fontFamily: 'Cairo',
      colorScheme: colorScheme,
      textTheme: textTheme,
      scaffoldBackgroundColor: colorScheme.background,
      appBarTheme: AppBarTheme(
        backgroundColor: colorScheme.primary,
        foregroundColor: colorScheme.onPrimary,
        elevation: 1.0,
        centerTitle: true,
        titleTextStyle: textTheme.headlineMedium,
        iconTheme: IconThemeData(color: colorScheme.onPrimary),
      ),
      bottomNavigationBarTheme: BottomNavigationBarThemeData(
        selectedItemColor: colorScheme.primary,
        unselectedItemColor: Colors.grey.shade500,
        backgroundColor: Colors.white,
        type: BottomNavigationBarType.fixed,
        elevation: 8.0,
        selectedLabelStyle: textTheme.labelMedium?.copyWith(fontSize: 12),
        unselectedLabelStyle: textTheme.labelMedium?.copyWith(fontSize: 12),
      ),
      cardTheme: CardTheme(
        elevation: 3.0,
        margin: const EdgeInsets.symmetric(vertical: 8.0, horizontal: 0),
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(16.0),
          side: BorderSide(color: Colors.grey.shade200, width: 0.5),
        ),
        color: colorScheme.surface,
        clipBehavior: Clip.antiAlias,
        shadowColor: Colors.black.withOpacity(0.1),
      ),
      elevatedButtonTheme: ElevatedButtonThemeData(
        style: ElevatedButton.styleFrom(
          backgroundColor: colorScheme.secondary,
          foregroundColor: colorScheme.onSecondary,
          padding: const EdgeInsets.symmetric(horizontal: 20.0, vertical: 12.0),
          shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(30.0),
          ),
          textStyle: textTheme.labelLarge?.copyWith(
            fontSize: 14,
            fontWeight: FontWeight.bold,
          ),
          elevation: 2.0,
          shadowColor: Colors.black.withOpacity(0.15),
        ),
      ),
      textButtonTheme: TextButtonThemeData(
        style: TextButton.styleFrom(
          foregroundColor: colorScheme.primary,
          textStyle: textTheme.labelMedium?.copyWith(
            fontWeight: FontWeight.bold,
            fontSize: 13,
          ),
          padding: const EdgeInsets.symmetric(horizontal: 10.0, vertical: 6.0),
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(8)),
        ),
      ),
      listTileTheme: ListTileThemeData(
        iconColor: colorScheme.secondary,
        titleTextStyle: textTheme.titleMedium?.copyWith(
          fontWeight: FontWeight.w600,
        ),
        subtitleTextStyle: textTheme.bodyMedium,
        dense: false,
        contentPadding: const EdgeInsets.symmetric(
          horizontal: 16.0,
          vertical: 8.0,
        ),
        horizontalTitleGap: 12.0,
      ),
      iconTheme: IconThemeData(color: colorScheme.secondary, size: 22.0),
      dividerTheme: DividerThemeData(
        color: Colors.grey.shade200,
        thickness: 1.0,
        space: 0,
      ),
      inputDecorationTheme: InputDecorationTheme(
        filled: true,
        fillColor: Colors.grey.shade50.withOpacity(0.5),
        border: OutlineInputBorder(
          borderRadius: BorderRadius.circular(12.0),
          borderSide: BorderSide.none,
        ),
        enabledBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(12.0),
          borderSide: BorderSide(color: Colors.grey.shade300, width: 1.0),
        ),
        focusedBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(12.0),
          borderSide: BorderSide(color: colorScheme.primary, width: 1.5),
        ),
        labelStyle: textTheme.bodyMedium?.copyWith(
          color: colorScheme.secondary.withOpacity(0.8),
        ),
        floatingLabelStyle: textTheme.bodyMedium?.copyWith(
          color: colorScheme.primary,
        ),
        hintStyle: textTheme.bodyMedium?.copyWith(color: Colors.grey.shade400),
      ),
      snackBarTheme: SnackBarThemeData(
        backgroundColor: colorScheme.secondary.withOpacity(0.95),
        contentTextStyle: textTheme.bodyMedium?.copyWith(color: Colors.white),
        actionTextColor: accentColor,
        shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
        behavior: SnackBarBehavior.floating,
        elevation: 4.0,
      ),
    );
  }
}

class SplashScreen extends StatefulWidget {
  @override
  _SplashScreenState createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> with SingleTickerProviderStateMixin {
  late AnimationController _animationController;
  late Animation<double> _fadeAnimation;
  late Animation<double> _scaleAnimation;

  @override
  void initState() {
    super.initState();

    _animationController = AnimationController(
      vsync: this,
      duration: Duration(milliseconds: 1500),
    );

    _fadeAnimation = Tween<double>(begin: 0.0, end: 1.0).animate(
      CurvedAnimation(parent: _animationController, curve: Curves.easeIn),
    );

    _scaleAnimation = Tween<double>(begin: 0.5, end: 1.0).animate(
      CurvedAnimation(parent: _animationController, curve: Curves.elasticOut),
    );

    _animationController.forward();

    Timer(
      Duration(seconds: 4),
      () {
        if (mounted) {
          Navigator.pushReplacementNamed(context, LoginScreen.routeName);
        }
      },
    );
  }

  @override
  void dispose() {
    _animationController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    SystemChrome.setSystemUIOverlayStyle(SystemUiOverlayStyle(
      statusBarColor: Colors.transparent,
      statusBarIconBrightness: Brightness.dark,
      systemNavigationBarColor: Color(0xFFF5F5F5),
      systemNavigationBarIconBrightness: Brightness.dark,
    ));

    return Scaffold(
      backgroundColor: Color(0xFFF5F5F5),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            ScaleTransition(
              scale: _scaleAnimation,
              child: FadeTransition(
                opacity: _fadeAnimation,
                child: Hero(
                  tag: 'app_logo',
                  child: Image.asset(
                    'assets/77.png',
                    width: MediaQuery.of(context).size.width * 0.5,
                    fit: BoxFit.contain,
                  ),
                ),
              ),
            ),
            SizedBox(height: 40),

            FadeTransition(
              opacity: _fadeAnimation,
              child: Padding(
                padding: const EdgeInsets.symmetric(horizontal: 40.0),
                child: Text(
                  'مرحباً بك في تطبيقنا المميز!',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 22,
                    fontWeight: FontWeight.w600,
                    color: Colors.teal.shade700,
                  ),
                ),
              ),
            ),
            SizedBox(height: 20),

            FadeTransition(
              opacity: _fadeAnimation,
              child: SizedBox(
                width: 50,
                height: 50,
                child: CircularProgressIndicator(
                  strokeWidth: 3.0,
                  valueColor: AlwaysStoppedAnimation<Color>(Colors.teal.shade500),
                ),
              ),
            ),
            SizedBox(height: 15),
            FadeTransition(
              opacity: _fadeAnimation,
              child: Text(
                'جاري التجهيز...',
                style: TextStyle(
                  fontSize: 16,
                  color: Colors.grey[600],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

#### `lib/screens/authentication/login_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:kids/screens/main_sections/home_page.dart'; // تم تغيير المسار
import 'package:kids/screens/authentication/signup_screen.dart'; // تم تغيير المسار
// يمكنك استخدام Provider للوصول إلى AuthProvider إذا تم تنفيذه
// import 'package:provider/provider.dart';
// import 'package:kids/providers/auth/auth_provider.dart';


class LoginScreen extends StatefulWidget {
  static const String routeName = '/login';

  @override
  _LoginScreenState createState() => _LoginScreenState();
}

class _LoginScreenState extends State<LoginScreen> {
  final _formKey = GlobalKey<FormState>();
  final TextEditingController _emailController = TextEditingController();
  final TextEditingController _passwordController = TextEditingController();
  bool _obscurePassword = true;

  @override
  void dispose() {
    _emailController.dispose();
    _passwordController.dispose();
    super.dispose();
  }

  void _togglePasswordVisibility() {
    setState(() {
      _obscurePassword = !_obscurePassword;
    });
  }

  void _attemptLogin() {
    if (_formKey.currentState!.validate()) {
      // String email = _emailController.text;
      // String password = _passwordController.text;
      // // مثال على استخدام Provider
      // final authProvider = Provider.of<AuthProvider>(context, listen: false);
      // authProvider.login(email, password, 'FlutterApp').then((_) {
      //   Navigator.pushReplacementNamed(context, HomePage.routeName);
      // }).catchError((error) {
      //   ScaffoldMessenger.of(context).showSnackBar(
      //     SnackBar(content: Text('فشل تسجيل الدخول: $error')),
      //   );
      // });

      // محاكاة تسجيل الدخول الناجح
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('جارٍ تسجيل الدخول... (محاكاة)')),
      );
      // الانتقال إلى الصفحة الرئيسية بعد تسجيل الدخول (حتى لو كانت المحاكاة فقط)
      Navigator.pushReplacementNamed(context, HomePage.routeName);
    }
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: Text('تسجيل الدخول'),
        // يمكنك إزالة زر الرجوع إذا كانت هذه هي أول شاشة بعد SplashScreen
        automaticallyImplyLeading: false, // لا تظهر زر الرجوع افتراضيًا
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(20.0),
          child: Form(
            key: _formKey,
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: [
                Hero( // تأكد من وجود Hero tag هنا إذا كنت تستخدمها في SplashScreen
                  tag: 'app_logo',
                  child: Image.asset(
                    'assets/77.png', // نفس مسار الشعار من SplashScreen
                    height: 120,
                    width: 120,
                    fit: BoxFit.contain,
                  ),
                ),
                SizedBox(height: 20),
                Text(
                  'مرحباً بك مجدداً',
                  textAlign: TextAlign.center,
                  style: theme.textTheme.displaySmall?.copyWith(color: theme.colorScheme.primary),
                ),
                SizedBox(height: 10),
                Text(
                  'الرجاء إدخال بيانات الاعتماد الخاصة بك للمتابعة',
                  textAlign: TextAlign.center,
                  style: theme.textTheme.bodyLarge?.copyWith(color: Colors.grey[700]),
                ),
                SizedBox(height: 40),
                TextFormField(
                  controller: _emailController,
                  decoration: InputDecoration(
                    labelText: 'البريد الإلكتروني أو اسم المستخدم',
                    hintText: 'ادخل بريدك الإلكتروني أو اسم المستخدم',
                    prefixIcon: Icon(Icons.person_outline),
                  ),
                  keyboardType: TextInputType.emailAddress,
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return 'الرجاء إدخال البريد الإلكتروني أو اسم المستخدم';
                    }
                    return null;
                  },
                ),
                SizedBox(height: 20),
                TextFormField(
                  controller: _passwordController,
                  obscureText: _obscurePassword,
                  decoration: InputDecoration(
                    labelText: 'كلمة المرور',
                    hintText: 'ادخل كلمة المرور الخاصة بك',
                    prefixIcon: Icon(Icons.lock_outline),
                    suffixIcon: IconButton(
                      icon: Icon(
                        _obscurePassword ? Icons.visibility_off : Icons.visibility,
                      ),
                      onPressed: _togglePasswordVisibility,
                    ),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return 'الرجاء إدخال كلمة المرور';
                    }
                    if (value.length < 6) {
                      return 'يجب أن تكون كلمة المرور 6 أحرف على الأقل';
                    }
                    return null;
                  },
                ),
                SizedBox(height: 30),
                ElevatedButton(
                  onPressed: _attemptLogin,
                  child: Text('تسجيل الدخول'),
                ),
                SizedBox(height: 20),
                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    TextButton(
                      onPressed: () {
                        ScaffoldMessenger.of(context).showSnackBar(
                          SnackBar(content: Text('سيتم إعادة تعيين كلمة المرور لاحقاً')),
                        );
                      },
                      child: Text('هل نسيت كلمة المرور؟'),
                    ),
                    TextButton(
                      onPressed: () {
                        Navigator.pushNamed(context, SignUpScreen.routeName);
                      },
                      child: Text('إنشاء حساب جديد'),
                    ),
                  ],
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

#### `lib/screens/authentication/signup_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:kids/screens/authentication/login_screen.dart'; // تم تغيير المسار

class SignUpScreen extends StatelessWidget {
  static const String routeName = '/signup'; // إضافة اسم للمسار

  final TextEditingController _fullNameController = TextEditingController();
  final TextEditingController _emailController = TextEditingController();
  final TextEditingController _phoneController = TextEditingController();
  final TextEditingController _passwordController = TextEditingController();
  final TextEditingController _confirmPasswordController = TextEditingController();
  final _formKey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      extendBodyBehindAppBar: true, // لجعل الـ body يمتد خلف الـ app bar
      appBar: AppBar(
        backgroundColor: Colors.transparent, // جعل الخلفية شفافة
        elevation: 0, // إزالة الظل
        leading: IconButton(
          icon: Icon(Icons.arrow_back_ios, color: Colors.white), // لون أيقونة الرجوع
          onPressed: () => Navigator.pop(context),
        ),
      ),
      body: Stack(
        children: [
          Positioned.fill(
            child: Image.asset(
              'assets/5.png',
              fit: BoxFit.cover,
            ),
          ),
          Container(
            color: Colors.black.withOpacity(0.5),
          ),
          Center(
            child: SingleChildScrollView(
              padding: EdgeInsets.all(20),
              child: Form(
                key: _formKey,
                child: Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    Text(
                      'إنشاء حساب ولي أمر',
                      textAlign: TextAlign.center,
                      style: theme.textTheme.headlineMedium?.copyWith(
                        color: Colors.white,
                        fontSize: 26,
                      ),
                    ),
                    SizedBox(height: 20),

                    _buildTextField(
                      controller: _fullNameController,
                      labelText: 'الاسم الكامل',
                      icon: Icons.person,
                      validator: (value) {
                        if (value == null || value.isEmpty) return 'الرجاء إدخال الاسم الكامل';
                        return null;
                      },
                    ),
                    SizedBox(height: 15),

                    _buildTextField(
                      controller: _emailController,
                      labelText: 'البريد الإلكتروني',
                      icon: Icons.email,
                      keyboardType: TextInputType.emailAddress,
                      validator: (value) {
                        if (value == null || value.isEmpty) return 'الرجاء إدخال البريد الإلكتروني';
                        if (!RegExp(r'^[^@]+@[^@]+\.[^@]+').hasMatch(value)) return 'الرجاء إدخال بريد إلكتروني صحيح';
                        return null;
                      },
                    ),
                    SizedBox(height: 15),

                    _buildTextField(
                      controller: _phoneController,
                      labelText: 'رقم الهاتف',
                      icon: Icons.phone,
                      keyboardType: TextInputType.phone,
                      validator: (value) {
                        if (value == null || value.isEmpty) return 'الرجاء إدخال رقم الهاتف';
                        return null;
                      },
                    ),
                    SizedBox(height: 15),

                    _buildTextField(
                      controller: _passwordController,
                      labelText: 'كلمة المرور',
                      icon: Icons.lock,
                      obscureText: true,
                      validator: (value) {
                        if (value == null || value.isEmpty) return 'الرجاء إدخال كلمة المرور';
                        if (value.length < 8) return 'يجب أن تكون كلمة المرور 8 أحرف على الأقل';
                        return null;
                      },
                    ),
                    SizedBox(height: 15),

                    _buildTextField(
                      controller: _confirmPasswordController,
                      labelText: 'تأكيد كلمة المرور',
                      icon: Icons.lock,
                      obscureText: true,
                      validator: (value) {
                        if (value == null || value.isEmpty) return 'الرجاء تأكيد كلمة المرور';
                        if (value != _passwordController.text) return 'كلمتا المرور غير متطابقتين';
                        return null;
                      },
                    ),
                    SizedBox(height: 25),

                    ElevatedButton(
                      onPressed: () {
                        if (_formKey.currentState!.validate()) {
                          // TODO: منطق إنشاء حساب جديد (API call)
                          ScaffoldMessenger.of(context).showSnackBar(
                            SnackBar(content: Text('تم إنشاء الحساب بنجاح (محاكاة)!')),
                          );
                          Navigator.pushReplacementNamed(context, LoginScreen.routeName);
                        }
                      },
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.white,
                        foregroundColor: theme.colorScheme.primary, // لون النص يتوافق مع ثيم التطبيق
                        padding: EdgeInsets.symmetric(vertical: 15),
                        shape: RoundedRectangleBorder(
                          borderRadius: BorderRadius.circular(12),
                        ),
                      ),
                      child: Text(
                        'إنشاء حساب جديد',
                        style: theme.textTheme.labelLarge?.copyWith(fontSize: 18),
                      ),
                    ),
                    SizedBox(height: 20),

                    TextButton(
                      onPressed: () {
                        Navigator.pushReplacementNamed(context, LoginScreen.routeName);
                      },
                      child: Text(
                        'تسجيل الدخول بدلا من ذلك',
                        style: theme.textTheme.labelLarge?.copyWith(color: Colors.white.withOpacity(0.9)),
                      ),
                    ),
                  ],
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }

  Widget _buildTextField({
    required TextEditingController controller,
    required String labelText,
    required IconData icon,
    TextInputType keyboardType = TextInputType.text,
    bool obscureText = false,
    String? Function(String?)? validator,
  }) {
    return TextFormField(
      controller: controller,
      keyboardType: keyboardType,
      obscureText: obscureText,
      textAlign: TextAlign.right, // RTL
      textDirection: TextDirection.rtl, // RTL
      decoration: InputDecoration(
        labelText: labelText,
        prefixIcon: Icon(icon, color: Colors.grey.shade600), // لون أيقونات الحقول
        border: OutlineInputBorder(
          borderRadius: BorderRadius.circular(12),
        ),
        fillColor: Colors.white.withOpacity(0.9), // خلفية الحقل شبه شفافة
        filled: true,
        labelStyle: TextStyle(color: Colors.grey.shade700), // لون نص الـ Label
        hintStyle: TextStyle(color: Colors.grey.shade500),
      ),
      style: TextStyle(color: Colors.black87), // لون النص المدخل
      validator: validator,
    );
  }
}
```

#### `lib/screens/main_sections/home_page.dart`

```dart
import 'package:flutter/material.dart';
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:kids/screens/child_features/attendance_log_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/health_records_timeline_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/messaging/gmail_inbox_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/main_sections/weekly_schedule_page.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/student_activity_schedule_page.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/educational_resources_list_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/class_overview_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/daily_meal_record_page.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/upcoming_events_mobile_screen.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/health_dashboard_page.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/teacher_notes_display_page.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/games_gallery.dart'; // تم تحديث المسار
import 'package:kids/screens/child_features/child_profile_screen.dart'; // تم تحديث المسار

class HomePage extends StatefulWidget {
  static const String routeName = '/home';
  const HomePage({super.key});
  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  int _currentIndex = 0;

  final List<Widget> _sections = [
    const HomeSection(),
    WeeklySchedulePage(),
    GmailInboxScreen(), // هذه هي الشاشة المحدثة للرسائل
    ChildProfileScreen(),
  ];

  void _onItemTapped(int index) {
    if (index >= 0 && index < _sections.length && index != _currentIndex) {
      setState(() {
        _currentIndex = index;
      });
    }
  }

  void _navigateTo(BuildContext context, Widget page) {
    if (Scaffold.of(context).isDrawerOpen) {
      Navigator.pop(context);
    }

    // تحقق إذا كانت الصفحة هي إحدى أقسام الـ BottomNavigationBar
    int sectionIndex = _sections.indexWhere(
      (s) => s.runtimeType == page.runtimeType,
    );

    if (sectionIndex != -1) {
      // إذا كانت الصفحة موجودة في الـ BottomNavigationBar، انتقل إليها مباشرة
      if (_currentIndex != sectionIndex) {
        setState(() {
          _currentIndex = sectionIndex;
        });
      }
    } else {
      // إذا لم تكن الصفحة جزءاً من الـ BottomNavigationBar، قم بالانتقال إليها باستخدام Navigator.push
      Navigator.of(
        context,
        rootNavigator: false, // احتفظ بالنافغاتور الحالي في ستاك الـ Navigator
      ).push(MaterialPageRoute(builder: (context) => page));
    }
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    String appBarTitle;
    switch (_currentIndex) {
      case 0:
        appBarTitle = 'الصفحة الرئيسية';
        break;
      case 1:
        appBarTitle = 'الجدول الأسبوعي';
        break;
      case 2:
        appBarTitle = 'التواصل';
        break;
      case 3:
        appBarTitle = 'الحساب الشخصي';
        break;
      default:
        appBarTitle = 'روضة الأطفال';
    }

    return Scaffold(
      appBar: AppBar(
        title: Text(appBarTitle),
        actions: [
          if (_currentIndex == 0)
            IconButton(
              icon: const Icon(Icons.notifications_none_outlined),
              tooltip: 'الإشعارات',
              onPressed: () => ScaffoldMessenger.of(context).showSnackBar(
                const SnackBar(
                  content: Text('لا توجد إشعارات جديدة حالياً'),
                ),
              ),
            ),
          const SizedBox(width: 8),
        ],
      ),
      drawer: Builder(
        builder: (drawerContext) => _buildAppDrawer(drawerContext, theme),
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _currentIndex,
        onTap: _onItemTapped,
        items: const [
          BottomNavigationBarItem(
            icon: Icon(Icons.home_outlined),
            activeIcon: Icon(Icons.home),
            label: 'الرئيسية',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.calendar_today_outlined),
            activeIcon: Icon(Icons.calendar_today),
            label: 'الجدول',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.chat_bubble_outline),
            activeIcon: Icon(Icons.chat_bubble),
            label: 'التواصل',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.account_circle_outlined),
            activeIcon: Icon(Icons.account_circle),
            label: 'الحساب',
          ),
        ],
      ),
      body: SafeArea(
        child: IndexedStack(index: _currentIndex, children: _sections),
      ),
    );
  }

  Widget _buildAppDrawer(BuildContext context, ThemeData theme) {
    return Drawer(
      backgroundColor: theme.colorScheme.surface,
      child: ListView(
        padding: EdgeInsets.zero,
        children: [
          DrawerHeader(
            decoration: BoxDecoration(
              gradient: LinearGradient(
                colors: [
                  theme.colorScheme.primary,
                  theme.colorScheme.primary.withOpacity(0.8),
                ],
                begin: AlignmentDirectional.topStart,
                end: AlignmentDirectional.bottomEnd,
              ),
            ),
            child: Column(
              mainAxisAlignment: MainAxisAlignment.end,
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Padding(
                  padding: const EdgeInsets.only(bottom: 12.0),
                  child: Text(
                    'القائمة الرئيسية',
                    style: theme.textTheme.headlineMedium?.copyWith(
                      color: theme.colorScheme.onPrimary,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
              ],
            ),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.restaurant_menu_outlined,
            text: 'الوجبات',
            onTap: () => _navigateTo(context, DailyMealRecordPage()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.photo_library_outlined,
            text: 'الوسائط اليومية',
            onTap: () => _navigateTo(context, ClassOverviewScreen()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.local_activity_outlined,
            text: 'الانشطة اليومية',
            onTap: () => _navigateTo(context, StudentActivitySchedulePage()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.fact_check_outlined,
            text: 'الحضور والغياب',
            onTap: () => _navigateTo(context, AttendanceLogScreen()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.note_alt_outlined,
            text: 'قائمة الملاحظات',
            onTap: () => _navigateTo(context, const TeacherNotesDisplayPage()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.monitor_heart_outlined,
            text: 'المؤشرات الصحية',
            onTap: () => _navigateTo(context, HealthDashboardPage()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.history_edu_outlined,
            text: 'السجل الصحي',
            onTap: () => _navigateTo(context, HealthRecordsTimelineLeftTimeline()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.menu_book_outlined,
            text: ' المواد',
            onTap: () => _navigateTo(context, EducationalResourcesListScreen()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.event_outlined,
            text: 'الفعاليات',
            onTap: () => _navigateTo(context, UpcomingEventsMobileScreen()),
          ),
          _buildDrawerItem(
            context: context,
            icon: Icons.sports_esports_outlined,
            text: 'الألعاب التعليمية',
            onTap: () => _navigateTo(context, GamesGallery()),
          ),

          const Divider(indent: 16, endIndent: 16, thickness: 0.5),

          _buildDrawerItem(
            context: context,
            icon: Icons.logout,
            text: 'تسجيل الخروج',
            onTap: () {
              Navigator.pop(context);
              // TODO: إضافة منطق تسجيل الخروج الفعلي هنا (مثل استدعاء AuthProvider.logout())
              ScaffoldMessenger.of(context).showSnackBar(
                const SnackBar(content: Text('تم تسجيل الخروج (مثال)')),
              );
            },
          ),
        ],
      ),
    );
  }

  Widget _buildDrawerItem({
    required BuildContext context,
    required IconData icon,
    required String text,
    required VoidCallback onTap,
  }) {
    // final theme = Theme.of(context); // لم نعد نستخدم الثيم هنا مباشرة

    return ListTile(
      leading: Icon(icon),
      title: Text(text),
      onTap: onTap,
      dense: true,
      visualDensity: VisualDensity.compact,
      contentPadding: const EdgeInsetsDirectional.only(
        start: 20,
        end: 16,
        top: 4,
        bottom: 4,
      ),
    );
  }
}

class HomeSection extends StatelessWidget {
  const HomeSection({super.key});

  void _navigateToPage(BuildContext context, Widget page) {
    // يجب أن تكون هذه الصفحة قابلة للـ pop للعودة لـ HomeSection
    Navigator.push(context, MaterialPageRoute(builder: (context) => page));
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    final textTheme = theme.textTheme;
    final colorScheme = theme.colorScheme;
    final String childName = "طفلي الرائع";

    return SingleChildScrollView(
      padding: const EdgeInsets.all(16.0),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          _buildWelcomeHeader(context, textTheme, childName, colorScheme),
          const SizedBox(height: 20.0),

          _buildKeySummaries(context, theme),
          const SizedBox(height: 24.0),

          _buildSectionHeader(
            context,
            'أحدث الملاحظات',
            Icons.campaign_outlined,
            () => _navigateToPage(context, const TeacherNotesDisplayPage()),
          ),
          _buildNotesContent(context),
          const SizedBox(height: 24.0),

          _buildSectionHeader(
            context,
            'لمحة عن اليوم',
            Icons.today_outlined,
            () => _navigateToPage(context, WeeklySchedulePage()),
          ),
          _buildScheduleContent(context),
          const SizedBox(height: 24.0),

          _buildSectionHeader(
            context,
            'صور من يومنا',
            Icons.photo_library_outlined,
            // تغيير إلى StudentMediaGalleryScreen للصفحة الكاملة
            () => _navigateToPage(context, const StudentMediaGalleryScreen()),
          ),
          _buildPhotoGrid(context),
          const SizedBox(height: 24.0),

          _buildSectionHeader(
            context,
            'أنشطة مقترحة',
            Icons.lightbulb_outline,
            () => _navigateToPage(context, GamesGallery()),
          ),
          _buildActivitiesContent(context),
          const SizedBox(height: 16.0),
        ],
      ),
    );
  }

  Widget _buildWelcomeHeader(
    BuildContext context,
    TextTheme textTheme,
    String name,
    ColorScheme colorScheme,
  ) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.spaceBetween,
      crossAxisAlignment: CrossAxisAlignment.center,
      children: [
        Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              'مرحباً بعودتك،',
              style: textTheme.bodyLarge?.copyWith(
                color: colorScheme.secondary,
              ),
            ),
            Text(name, style: textTheme.displaySmall?.copyWith(height: 1.1)),
          ],
        ),
        CircleAvatar(
          radius: 28,
          backgroundColor: colorScheme.primary.withOpacity(0.15),
          child: CircleAvatar(
            radius: 25,
            backgroundColor: colorScheme.primary,
            child: Text(
              name.isNotEmpty ? name[0] : 'ط',
              style: const TextStyle(
                fontSize: 22,
                color: Colors.white,
                fontWeight: FontWeight.bold,
              ),
            ),
          ),
        ),
      ],
    );
  }

  Widget _buildKeySummaries(BuildContext context, ThemeData theme) {
    final nextScheduleItem = ScheduleItemData(
      time: '10:30 ص',
      activity: '🍎 وجبة خفيفة',
      icon: Icons.restaurant_menu,
    );
    final latestNote =
        'لا تنسوا إحضار قبعة الشمس غداً ☀️ ليوم اللعب في الخارج.';
    return IntrinsicHeight(
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Expanded(
            child: _buildSummaryCard(
              context: context,
              theme: theme,
              icon: nextScheduleItem.icon,
              title: 'التالي في الجدول:',
              content:
                  '${nextScheduleItem.activity} (${nextScheduleItem.time})',
              onTap: () => _navigateToPage(context, WeeklySchedulePage()),
              backgroundColor: theme.colorScheme.tertiary.withOpacity(0.1),
              iconColor: theme.colorScheme.tertiary,
            ),
          ),
          const SizedBox(width: 12.0),
          Expanded(
            child: _buildSummaryCard(
              context: context,
              theme: theme,
              icon: Icons.notifications_active_outlined,
              title: 'آخر ملاحظة:',
              onTap: () => _navigateToPage(context, const TeacherNotesDisplayPage()),
              content: latestNote,
              backgroundColor: theme.colorScheme.secondary.withOpacity(0.1),
              iconColor: theme.colorScheme.secondary,
            ),
          ),
        ],
      ),
    );
  }

  Widget _buildSummaryCard({
    required BuildContext context,
    required ThemeData theme,
    required IconData icon,
    required String title,
    required String content,
    required VoidCallback onTap,
    Color? backgroundColor,
    Color? iconColor,
  }) {
    return Card(
      color: backgroundColor ?? theme.cardTheme.color,
      elevation: 2.0,
      child: InkWell(
        onTap: onTap,
        borderRadius: BorderRadius.circular(16.0),
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Row(
                crossAxisAlignment: CrossAxisAlignment.center,
                children: [
                  Icon(
                    icon,
                    size: 22.0,
                    color: iconColor ?? theme.colorScheme.primary,
                  ),
                  const SizedBox(width: 8.0),
                  Expanded(
                    child: Text(
                      title,
                      style: theme.textTheme.bodyMedium?.copyWith(
                        fontWeight: FontWeight.bold,
                        color: (iconColor ?? theme.colorScheme.primary)
                            .withOpacity(0.9),
                      ),
                      maxLines: 1,
                      overflow: TextOverflow.ellipsis,
                    ),
                  ),
                ],
              ),
              const SizedBox(height: 10.0),
              Expanded(
                child: Text(
                  content,
                  style: theme.textTheme.titleMedium?.copyWith(height: 1.35),
                  maxLines: 3,
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }

  Widget _buildSectionHeader(
    BuildContext context,
    String title,
    IconData? icon,
    VoidCallback? onViewAll,
  ) {
    final theme = Theme.of(context);
    return Padding(
      padding: const EdgeInsets.only(bottom: 12.0, top: 8.0),
      child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        crossAxisAlignment: CrossAxisAlignment.center,
        children: [
          Row(
            children: [
              if (icon != null)
                Icon(icon, color: theme.colorScheme.primary, size: 20),
              if (icon != null) const SizedBox(width: 8.0),
              Text(title, style: theme.textTheme.headlineSmall),
            ],
          ),
          if (onViewAll != null)
            TextButton(onPressed: onViewAll, child: const Text('عرض الكل')),
        ],
      ),
    );
  }

  Widget _buildNotesContent(BuildContext context) {
    final theme = Theme.of(context);
    final notes = [
      'تذكير: لا تنسوا إحضار قبعة الشمس غداً ☀️ ليوم اللعب في الخارج.',
      'الخميس القادم: رحلة إلى حديقة الحيوانات 🦒 (مطلوب موافقة الأهل المسبقة).',
      'تم إضافة صور جديدة لنشاط الصلصال في المعرض 🖼️، شاهدوا إبداعات أطفالكم!',
    ];
    if (notes.isEmpty) {
      return const _EmptySectionPlaceholder(
        message: "لا توجد ملاحظات جديدة حالياً.",
      );
    }

    return Container(
      decoration: BoxDecoration(
        color: theme.cardTheme.color,
        borderRadius: BorderRadius.circular(16.0),
        border: Border.all(color: Colors.grey.shade200, width: 0.5),
      ),
      child: Column(
        children: List.generate(notes.length > 3 ? 3 : notes.length, (index) {
          bool isLast = index == (notes.length > 3 ? 2 : notes.length - 1);
          return Column(
            children: [
              ListTile(
                leading: Padding(
                  padding: const EdgeInsets.only(top: 4.0),
                  child: Icon(
                    Icons.info_outline,
                    color: theme.colorScheme.primary,
                    size: 20,
                  ),
                ),
                title: Text(notes[index], style: theme.textTheme.titleMedium),
                dense: true,
                contentPadding: const EdgeInsets.symmetric(
                  horizontal: 16,
                  vertical: 10,
                ),
              ),
              if (!isLast) const Divider(height: 1, indent: 16, endIndent: 16),
            ],
          );
        }),
      ),
    );
  }

  Widget _buildScheduleContent(BuildContext context) {
    final theme = Theme.of(context);
    final schedule = [
      ScheduleItemData(
        time: '09:30 ص',
        activity: '🎵 حلقة صباحية وأناشيد تعليمية',
        icon: Icons.music_note,
      ),
      ScheduleItemData(
        time: '10:30 ص',
        activity: '🍎 وجبة خفيفة وصحية (فواكه)',
        icon: Icons.restaurant_menu,
      ),
      ScheduleItemData(
        time: '11:00 ص',
        activity: '🎨 نشاط فني: تلوين ورسم حر',
        icon: Icons.palette_outlined,
      ),
    ];
    if (schedule.isEmpty) {
      return const _EmptySectionPlaceholder(
        message: "لا يوجد جدول محدد لليوم.",
      );
    }

    return Container(
      decoration: BoxDecoration(
        color: theme.cardTheme.color,
        borderRadius: BorderRadius.circular(16.0),
        border: Border.all(color: Colors.grey.shade200, width: 0.5),
      ),
      child: Column(
        children: List.generate(schedule.length > 3 ? 3 : schedule.length, (
          index,
        ) {
          bool isLast =
              index == (schedule.length > 3 ? 2 : schedule.length - 1);
          return Column(
            children: [
              Padding(
                padding: const EdgeInsets.symmetric(
                  horizontal: 16.0,
                  vertical: 12.0,
                ),
                child: ScheduleItem(data: schedule[index]),
              ),
              if (!isLast) const Divider(height: 1, indent: 16, endIndent: 16),
            ],
          );
        }),
      ),
    );
  }

  Widget _buildActivitiesContent(BuildContext context) {
    final theme = Theme.of(context);
    final activities = [
      ActivityItemData(
        title: 'اللعب بالرمل والماء',
        description: 'تنمية المهارات الحسية والحركية الدقيقة.',
        icon: Icons.beach_access_outlined,
      ),
      ActivityItemData(
        title: 'بناء المكعبات الملونة',
        description: 'تشجيع الإبداع والتفكير المنطقي وحل المشكلات البسيطة.',
        icon: Icons.construction_outlined,
      ),
      ActivityItemData(
        title: 'قراءة قصة تفاعلية',
        description: 'تنمية مهارات الاستماع والخيال واللغة.',
        icon: Icons.menu_book_outlined,
      ),
    ];
    if (activities.isEmpty) {
      return const _EmptySectionPlaceholder(
        message: "لا توجد أنشطة مقترحة حالياً.",
      );
    }

    return Container(
      decoration: BoxDecoration(
        color: theme.cardTheme.color,
        borderRadius: BorderRadius.circular(16.0),
        border: Border.all(color: Colors.grey.shade200, width: 0.5),
      ),
      child: Column(
        children: List.generate(activities.length > 3 ? 3 : activities.length, (
          index,
        ) {
          bool isLast =
              index == (activities.length > 3 ? 2 : activities.length - 1);
          return Column(
            children: [
              Padding(
                padding: const EdgeInsets.symmetric(
                  horizontal: 16.0,
                  vertical: 14.0,
                ),
                child: ActivityItem(data: activities[index]),
              ),
              if (!isLast) const Divider(height: 1, indent: 16, endIndent: 16),
            ],
          );
        }),
      ),
    );
  }

  Widget _buildPhotoGrid(BuildContext context) {
    final images = [
      'assets/1.png',
      'assets/2.png',
      'assets/3.png',
      'assets/1.png',
    ];
    final theme = Theme.of(context);
    if (images.isEmpty) {
      return const _EmptySectionPlaceholder(
        message: "لا توجد صور جديدة بعد.",
        icon: Icons.photo_library_outlined,
      );
    }

    return GridView.builder(
      shrinkWrap: true,
      physics: const NeverScrollableScrollPhysics(),
      gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
        crossAxisCount: 2,
        crossAxisSpacing: 12.0,
        mainAxisSpacing: 12.0,
        childAspectRatio: 1.0,
      ),
      itemCount: images.length > 4 ? 4 : images.length,
      itemBuilder: (context, index) {
        if (index >= images.length) return const SizedBox.shrink();
        return ImageItem(imageUrl: images[index]);
      },
    );
  }
}

class _EmptySectionPlaceholder extends StatelessWidget {
  final String message;
  final IconData? icon;

  const _EmptySectionPlaceholder({required this.message, this.icon});

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Container(
      padding: const EdgeInsets.symmetric(vertical: 32.0, horizontal: 16.0),
      alignment: Alignment.center,
      decoration: BoxDecoration(
        color: theme.colorScheme.surfaceVariant.withOpacity(0.5),
        borderRadius: BorderRadius.circular(12.0),
      ),
      child: Column(
        mainAxisSize: MainAxisSize.min,
        children: [
          if (icon != null) Icon(icon, size: 36, color: Colors.grey.shade400),
          if (icon != null) const SizedBox(height: 12),
          Text(
            message,
            style: theme.textTheme.bodyMedium?.copyWith(
              color: Colors.grey.shade600,
            ),
            textAlign: TextAlign.center,
          ),
        ],
      ),
    );
  }
}

class ScheduleItemData {
  final String time;
  final String activity;
  final IconData icon;
  const ScheduleItemData({
    required this.time,
    required this.activity,
    required this.icon,
  });
}

class ActivityItemData {
  final String title;
  final String description;
  final IconData icon;
  const ActivityItemData({
    required this.title,
    required this.description,
    required this.icon,
  });
}

class ScheduleItem extends StatelessWidget {
  final ScheduleItemData data;
  const ScheduleItem({super.key, required this.data});

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Row(
      crossAxisAlignment: CrossAxisAlignment.center,
      children: [
        CircleAvatar(
          radius: 18,
          backgroundColor: theme.colorScheme.primary.withOpacity(0.1),
          child: Icon(data.icon, color: theme.colorScheme.primary, size: 18),
        ),
        const SizedBox(width: 12.0),
        Expanded(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(
                data.activity,
                style: theme.textTheme.titleMedium?.copyWith(
                  fontWeight: FontWeight.w600,
                ),
                textAlign: TextAlign.start,
              ),
              const SizedBox(height: 3.0),
              Text(
                data.time,
                style: theme.textTheme.bodySmall?.copyWith(
                  color: theme.colorScheme.primary.withOpacity(0.8),
                  fontWeight: FontWeight.w500,
                ),
                textAlign: TextAlign.start,
              ),
            ],
          ),
        ),
      ],
    );
  }
}

class ActivityItem extends StatelessWidget {
  final ActivityItemData data;
  const ActivityItem({super.key, required this.data});

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Row(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        CircleAvatar(
          radius: 22,
          backgroundColor: theme.colorScheme.secondary.withOpacity(0.1),
          child: Icon(data.icon, color: theme.colorScheme.secondary, size: 22),
        ),
        const SizedBox(width: 14.0),
        Expanded(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(
                data.title,
                style: theme.textTheme.titleLarge?.copyWith(fontSize: 16),
                textAlign: TextAlign.start,
              ),
              const SizedBox(height: 5.0),
              Text(
                data.description,
                style: theme.textTheme.bodyMedium?.copyWith(height: 1.4),
                textAlign: TextAlign.start,
              ),
            ],
          ),
        ),
      ],
    );
  }
}

class ImageItem extends StatelessWidget {
  final String imageUrl;
  const ImageItem({super.key, required this.imageUrl});

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Card(
      clipBehavior: Clip.antiAlias,
      elevation: 2.0,
      child: GridTile(
        child: Image.asset(
          imageUrl,
          fit: BoxFit.cover,
          errorBuilder: (context, error, stackTrace) {
            return Container(
              alignment: Alignment.center,
              color: theme.colorScheme.surfaceVariant,
              child: Icon(
                Icons.broken_image_outlined,
                color: theme.colorScheme.onSurfaceVariant.withOpacity(0.6),
                size: 30,
              ),
            );
          },
        ),
      ),
    );
  }
}
```

#### `lib/screens/main_sections/weekly_schedule_page.dart`

```dart
import 'package:flutter/material.dart';

class WeeklySchedulePage extends StatelessWidget {
  final Map<String, List<String>> weeklySchedule = {
    "الأحد": [
      "التحية والأنشطة الصباحية",
      "اللغة العربية",
      "استراحة خفيفة (وجبة)",
      "الفن والإبداع",
      "اللعب الحر",
    ],
    "الاثنين": [
      "التحية والأنشطة الصباحية",
      "الرياضيات (الأرقام والأشكال)",
      "استراحة خفيفة (وجبة)",
      "الحركات البدنية",
      "القصص والمسرح",
    ],
    "الثلاثاء": [
      "التحية والأنشطة الصباحية",
      "العلوم (استكشاف الطبيعة)",
      "استراحة خفيفة (وجبة)",
      "الأنشطة اليدوية",
      "اللعب المنظم",
    ],
    "الأربعاء": [
      "التحية والأنشطة الصباحية",
      "اللغة الإنجليزية",
      "استراحة خفيفة (وجبة)",
      "الموسيقى والغناء",
      "الأنشطة الترفيهية",
    ],
    "الخميس": [
      "التحية والأنشطة الصباحية",
      "مراجعة شاملة",
      "استراحة خفيفة (وجبة)",
      "أنشطة العمل الجماعي",
      "يوم الألعاب (داخلي أو خارجي)",
    ],
  };

  WeeklySchedulePage();

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: Text('الجدول الأسبوعي'),
        centerTitle: true,
        // يمكنك تعديل اللون ليتماشى مع الثيم
        backgroundColor: theme.colorScheme.primary.withOpacity(0.9),
      ),
      body: ListView.builder(
        itemCount: weeklySchedule.keys.length,
        itemBuilder: (context, index) {
          String day = weeklySchedule.keys.elementAt(index);
          return Card(
            margin: EdgeInsets.symmetric(vertical: 10, horizontal: 15),
            elevation: 4,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12),
            ),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch, // لجعل الهيدر يملأ العرض
              children: [
                Container(
                  padding: EdgeInsets.all(12.0),
                  decoration: BoxDecoration(
                    color: theme.colorScheme.secondary, // لون مخصص لهيدر اليوم
                    borderRadius: BorderRadius.vertical(top: Radius.circular(12)),
                  ),
                  child: Text(
                    day,
                    style: theme.textTheme.titleLarge?.copyWith(
                      color: Colors.white,
                      fontSize: 18,
                    ),
                    textAlign: TextAlign.center, // توسيط النص في الهيدر
                  ),
                ),
                Padding(
                  padding: const EdgeInsets.symmetric(vertical: 8.0, horizontal: 16.0),
                  child: Column(
                    children: weeklySchedule[day]!.map((activity) {
                      return Padding(
                        padding: const EdgeInsets.symmetric(vertical: 6.0),
                        child: Row(
                          crossAxisAlignment: CrossAxisAlignment.start,
                          children: [
                            Icon(
                              Icons.check_circle_outline,
                              color: theme.colorScheme.tertiary, // لون أيقونة النشاط
                              size: 20,
                            ),
                            const SizedBox(width: 12),
                            Expanded(
                              child: Text(
                                activity,
                                textAlign: TextAlign.right, // RTL
                                style: theme.textTheme.bodyMedium?.copyWith(
                                  color: Colors.black87,
                                ),
                              ),
                            ),
                          ],
                        ),
                      );
                    }).toList(),
                  ),
                ),
              ],
            ),
          );
        },
      ),
    );
  }
}
```

#### `lib/screens/child_features/child_profile_screen.dart`

```dart
import 'package:flutter/material.dart';

class ChildProfileScreen extends StatelessWidget {
  const ChildProfileScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);

    // --- أنماط النص من الثيم (أكثر مرونة) ---
    final TextStyle labelStyle = theme.textTheme.bodyMedium!.copyWith(
      color: Colors.black54,
    );
    final TextStyle valueStyle = theme.textTheme.titleMedium!.copyWith(
      color: Colors.black87,
      fontWeight: FontWeight.w500,
    );
    final TextStyle nameStyle = theme.textTheme.displaySmall!.copyWith(
      color: Colors.black87,
    );
    final TextStyle sectionTitleStyle = theme.textTheme.headlineSmall!.copyWith(
      color: Color(0xFF005662), // لون أزرق داكن مميز للعناوين (ثابت أو من الثيم)
    );
    // ----------------------------------------------------

    return Scaffold(
      appBar: AppBar(
        title: const Text('ملف الطفل'),
        centerTitle: true,
        // تستخدم ألوان الـ AppBar من الـ ThemeData العام.
      ),
      body: SingleChildScrollView(
        physics: const BouncingScrollPhysics(),
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            const CircleAvatar(
              radius: 60.0,
              backgroundImage: AssetImage('assets/child_placeholder.png'), // تأكد من وجود الصورة
              backgroundColor: Colors.blueGrey,
            ),
            const SizedBox(height: 16),
            Text('أحمد علي', style: nameStyle),
            const SizedBox(height: 12),

            _buildInfoSection(
              theme: theme, // تمرير الثيم
              children: [
                _buildDetailRow('تاريخ الميلاد:', '15-05-2022 (2 سنوات)', labelStyle, valueStyle),
                _buildDetailRow('الجنس:', 'Male', labelStyle, valueStyle),
                _buildDetailRowWithHighlight('الفصل:', 'الأطفال الصغار (أقل من 3)', labelStyle, valueStyle, theme),
                _buildDetailRow('تاريخ التسجيل:', '10-01-2024', labelStyle, valueStyle),
              ],
            ),

            const SizedBox(height: 24.0),

            _buildInfoSection(
              theme: theme, // تمرير الثيم
              title: 'معلومات ولي الأمر',
              icon: Icons.people_outline,
              sectionTitleStyle: sectionTitleStyle, // تمرير النمط
              children: [
                _buildDetailRow('الاسم:', 'ولي أمر ا', labelStyle, valueStyle),
                _buildDetailRow('البريد الإلكتروني:', 'parent1@example.com', labelStyle, valueStyle, isEmailOrPhone: true),
                _buildDetailRow('رقم الهاتف:', '3210-654-987', labelStyle, valueStyle, isEmailOrPhone: true),
              ],
            ),

            const SizedBox(height: 24.0),

            _buildInfoSection(
              theme: theme, // تمرير الثيم
              title: 'المعلومات الطبية',
              icon: Icons.medical_services_outlined,
              sectionTitleStyle: sectionTitleStyle, // تمرير النمط
              children: [
                _buildDetailRow('الحساسية:', 'حساسية الفول السوداني', labelStyle, valueStyle),
                _buildDetailRow('ملاحظات طبية:', 'لا يوجد', labelStyle, valueStyle),
              ],
            ),
            const SizedBox(height: 20),
          ],
        ),
      ),
      backgroundColor: theme.scaffoldBackgroundColor,
    );
  }

  /// ودجت لبناء قسم معلومات (مثل ولي الأمر أو الطبي)
  Widget _buildInfoSection({
    required ThemeData theme,
    String? title,
    IconData? icon,
    TextStyle? sectionTitleStyle, // تم تمرير النمط بشكل منفصل
    required List<Widget> children}) {
    return Card(
      elevation: 2.0,
      margin: const EdgeInsets.symmetric(vertical: 8.0),
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(12.0),
      ),
      child: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            if (title != null) ...[
              Row(
                children: [
                  if (icon != null) ...[
                    Icon(icon, color: sectionTitleStyle?.color ?? theme.colorScheme.secondary, size: 20),
                    const SizedBox(width: 8),
                  ],
                  Text(title, style: sectionTitleStyle),
                ],
              ),
              const Divider(height: 20, thickness: 1),
            ],
            ...children,
          ],
        ),
      ),
    );
  }

  /// ودجت لبناء صف تفاصيل (تسمية وقيمة)
  Widget _buildDetailRow(
    String label,
    String value,
    TextStyle labelStyle,
    TextStyle valueStyle, {
    bool isEmailOrPhone = false,
  }) {
    return Padding(
      padding: const EdgeInsets.symmetric(vertical: 6.0),
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          SizedBox(
            width: 110,
            child: Text(label, style: labelStyle),
          ),
          const SizedBox(width: 10),
          Expanded(
            child: Text(
              value,
              style: valueStyle,
              textDirection: isEmailOrPhone ? TextDirection.ltr : null,
              textAlign: isEmailOrPhone ? TextAlign.left : null,
            ),
          ),
        ],
      ),
    );
  }

  /// ودجت مخصص لصف الفصل مع التمييز
  Widget _buildDetailRowWithHighlight(
    String label,
    String value,
    TextStyle labelStyle,
    TextStyle valueStyle,
    ThemeData theme, // تم تمرير الثيم
  ) {
    return Padding(
      padding: const EdgeInsets.symmetric(vertical: 6.0),
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.center,
        children: [
          SizedBox(
            width: 110,
            child: Text(label, style: labelStyle),
          ),
          const SizedBox(width: 10),
          Expanded(
            child: Container(
              padding: const EdgeInsets.symmetric(horizontal: 10.0, vertical: 4.0),
              decoration: BoxDecoration(
                color: theme.colorScheme.tertiary.withOpacity(0.2), // استخدام لون من الثيم
                borderRadius: BorderRadius.circular(8.0),
              ),
              child: Text(
                value,
                style: valueStyle.copyWith(color: theme.colorScheme.tertiary, fontWeight: FontWeight.bold),
                textAlign: TextAlign.center,
              ),
            ),
          ),
        ],
      ),
    );
  }
}
```

#### `lib/screens/child_features/attendance_log_screen.dart`

```dart
import 'package:flutter/material.dart';

// 1. تعريف حالة الحضور (Enum)
enum AttendanceStatus { present, absent, late, excused }

// 2. تعريف كلاس سجل الحضور (بخصائص أبسط للمحاكاة)
class AttendanceRecord {
  final DateTime date;
  final AttendanceStatus status;
  final TimeOfDay? checkInTime;
  final TimeOfDay? checkOutTime;
  final String? notes;
  final String loggedBy;

  AttendanceRecord({
    required this.date,
    required this.status,
    this.checkInTime,
    this.checkOutTime,
    this.notes,
    required this.loggedBy,
  });
}

class AttendanceLogScreen extends StatelessWidget {
  AttendanceLogScreen({Key? key}) : super(key: key);

  final List<AttendanceRecord> attendanceRecords = [
    AttendanceRecord(
        date: DateTime(2025, 4, 29),
        status: AttendanceStatus.late,
        checkInTime: const TimeOfDay(hour: 9, minute: 0),
        checkOutTime: const TimeOfDay(hour: 15, minute: 0),
        notes: 'الطفل مشاغب بعض الشيء اليوم.',
        loggedBy: 'مدير النظام'),
    AttendanceRecord(
        date: DateTime(2025, 4, 28),
        status: AttendanceStatus.present,
        checkInTime: const TimeOfDay(hour: 8, minute: 25),
        checkOutTime: const TimeOfDay(hour: 15, minute: 5),
        notes: 'كان متعاوناً ومنتبهًا خلال الحصة.',
        loggedBy: 'المعلمة سارة'),
    AttendanceRecord(
        date: DateTime(2025, 4, 27),
        status: AttendanceStatus.absent,
        checkInTime: null,
        checkOutTime: null,
        notes: 'تغيب بسبب وعكة صحية حسب إفادة الأهل.',
        loggedBy: 'السكرتارية'),
    AttendanceRecord(
        date: DateTime(2025, 4, 26),
        status: AttendanceStatus.present,
        checkInTime: const TimeOfDay(hour: 8, minute: 15),
        checkOutTime: const TimeOfDay(hour: 14, minute: 55),
        notes: null,
        loggedBy: 'المعلمة سارة'),
  ];

  String _formatDate(DateTime date) {
    return "${date.year}-${date.month.toString().padLeft(2, '0')}-${date.day.toString().padLeft(2, '0')}";
  }

  String _formatTime(TimeOfDay? time) {
    if (time == null) return '--:--';
    return '${time.hour.toString().padLeft(2, '0')}:${time.minute.toString().padLeft(2, '0')}';
  }

  @override
  Widget build(BuildContext context) {
    final Color primaryColor = Theme.of(context).colorScheme.primary;

    return Scaffold(
      appBar: AppBar(
        title: const Text('سجل الحضور والغياب', style: TextStyle(fontWeight: FontWeight.bold)),
        centerTitle: true,
        backgroundColor: primaryColor,
        foregroundColor: Colors.white,
        elevation: 2,
        leading: Navigator.canPop(context)
            ? IconButton(
                icon: const Icon(Icons.arrow_back_ios_new_rounded),
                onPressed: () => Navigator.pop(context),
              )
            : null,
      ),
      body: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Padding(
            padding: const EdgeInsetsDirectional.fromSTEB(16.0, 16.0, 16.0, 8.0),
            child: Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                const Text(
                  'السجلات الأخيرة',
                  style: TextStyle(
                    fontSize: 20,
                    fontWeight: FontWeight.w700,
                    color: Colors.black87,
                  ),
                  textAlign: TextAlign.start,
                ),
                OutlinedButton(
                  onPressed: () {
                    // TODO: implement full record view
                    ScaffoldMessenger.of(context).showSnackBar(
                      SnackBar(content: Text('عرض كل السجلات ليس متاحًا بعد.')),
                    );
                  },
                  child: const Text('عرض الكل'),
                  style: OutlinedButton.styleFrom(
                    foregroundColor: primaryColor,
                    side: BorderSide(color: primaryColor),
                    padding: const EdgeInsets.symmetric(horizontal: 14, vertical: 10),
                    textStyle: const TextStyle(fontSize: 14, fontWeight: FontWeight.w600),
                    shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(8)),
                  ),
                ),
              ],
            ),
          ),
          Expanded(
            child: attendanceRecords.isEmpty
                ? Center(
                    child: Text(
                      'لا توجد سجلات حضور لعرضها.',
                      style: TextStyle(fontSize: 16, color: Colors.grey[600]),
                    ),
                  )
                : ListView.builder(
                    padding: const EdgeInsetsDirectional.fromSTEB(12.0, 8.0, 12.0, 8.0),
                    itemCount: attendanceRecords.length,
                    itemBuilder: (context, index) {
                      final record = attendanceRecords[index];
                      return _buildAttendanceCard(context, record);
                    },
                  ),
          ),
        ],
      ),
      backgroundColor: Colors.grey[100],
    );
  }

  Widget _buildAttendanceCard(BuildContext context, AttendanceRecord record) {
    return Card(
      margin: const EdgeInsets.only(bottom: 16.0),
      elevation: 2,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(12.0),
      ),
      child: Padding(
        padding: const EdgeInsetsDirectional.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              crossAxisAlignment: CrossAxisAlignment.center,
              children: [
                _buildStatusChip(record.status),
                Row(
                  mainAxisSize: MainAxisSize.min,
                  children: [
                    Text(
                      _formatDate(record.date),
                      style: const TextStyle(fontWeight: FontWeight.bold, fontSize: 16),
                    ),
                    const SizedBox(width: 8),
                    Icon(Icons.calendar_today_rounded, size: 18, color: Colors.grey[600]),
                  ],
                ),
              ],
            ),
            const Divider(height: 24, thickness: 0.7, color: Color.fromARGB(255, 224, 224, 224)),
            if (record.status != AttendanceStatus.absent)
              Padding(
                padding: const EdgeInsets.only(bottom: 12.0),
                child: Row(
                  children: [
                    Expanded(child: _buildTimeInfo('الدخول', record.checkInTime, Icons.login_rounded)),
                    const SizedBox(width: 16),
                    Expanded(child: _buildTimeInfo('الخروج', record.checkOutTime, Icons.logout_rounded)),
                  ],
                ),
              ),
            if (record.notes?.isNotEmpty ?? false)
              Padding(
                padding: const EdgeInsets.only(bottom: 10.0),
                child: _buildInfoRow(Icons.sticky_note_2_outlined, 'ملاحظات', record.notes!),
              ),
            _buildInfoRow(Icons.person_outline_rounded, 'سُجل بواسطة', record.loggedBy),
          ],
        ),
      ),
    );
  }

  Widget _buildTimeInfo(String label, TimeOfDay? time, IconData icon) {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.center,
      children: [
        Text(
          label,
          style: TextStyle(fontSize: 13, color: Colors.grey[700]),
        ),
        const SizedBox(height: 6),
        Row(
          mainAxisSize: MainAxisSize.min,
          children: [
            Text(
              _formatTime(time),
              textDirection: TextDirection.ltr,
              style: const TextStyle(fontSize: 15, fontWeight: FontWeight.w500, letterSpacing: 0.6),
            ),
            const SizedBox(width: 6),
            Icon(icon, size: 18, color: Colors.blueGrey),
          ],
        ),
      ],
    );
  }

  Widget _buildInfoRow(IconData icon, String label, String value) {
    return Row(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Icon(icon, size: 18, color: Colors.grey[600]),
        const SizedBox(width: 10),
        Expanded(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(
                label + ':',
                style: TextStyle(fontSize: 14, color: Colors.grey[700], fontWeight: FontWeight.w500),
                textAlign: TextAlign.start,
              ),
              const SizedBox(height: 2),
              Text(
                value,
                style: const TextStyle(fontSize: 14, color: Colors.black87, height: 1.3),
                textAlign: TextAlign.start,
              ),
            ],
          ),
        ),
      ],
    );
  }

  Widget _buildStatusChip(AttendanceStatus status) {
    String text;
    Color backgroundColor;
    Color textColor;

    switch (status) {
      case AttendanceStatus.present:
        text = 'حاضر';
        backgroundColor = Colors.green.shade100;
        textColor = Colors.green.shade800;
        break;
      case AttendanceStatus.absent:
        text = 'غائب';
        backgroundColor = Colors.red.shade100;
        textColor = Colors.red.shade800;
        break;
      case AttendanceStatus.late:
        text = 'متأخر';
        backgroundColor = const Color(0xFFFFF9C4);
        textColor = const Color(0xFFF9A825);
        break;
      case AttendanceStatus.excused:
        text = 'معذور';
        backgroundColor = Colors.blue.shade100;
        textColor = Colors.blue.shade800;
        break;
    }

    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 12.0, vertical: 6.0),
      decoration: BoxDecoration(
        color: backgroundColor,
        borderRadius: BorderRadius.circular(15.0),
      ),
      child: Text(
        text,
        style: TextStyle(
          color: textColor,
          fontSize: 13,
          fontWeight: FontWeight.bold,
        ),
      ),
    );
  }
}
```

#### `lib/screens/child_features/health_dashboard_page.dart`

```dart
import 'package:flutter/material.dart';
import 'package:percent_indicator/circular_percent_indicator.dart';
import 'package:font_awesome_flutter/font_awesome_flutter.dart';
// لا توجد حاجة لـ url_launcher هنا بما أن الرابط لا يعمل
// import 'package:url_launcher/url_launcher.dart';

class HealthDashboardPage extends StatelessWidget {
  final Map<String, double> indicators = {
    'الأكل': 0.2,
    'الشرب': 0.4,
    'النشاط': 0.7,
    'الصحة النفسية': 0.9,
    'السمع': 0.85,
    'البصر': 0.5,
  };

  final Map<String, IconData> icons = {
    'الأكل': FontAwesomeIcons.utensils,
    'الشرب': FontAwesomeIcons.tint,
    'النشاط': FontAwesomeIcons.running,
    'الصحة النفسية': FontAwesomeIcons.smileBeam,
    'السمع': FontAwesomeIcons.earListen,
    'البصر': FontAwesomeIcons.eye,
  };

  final Map<String, Color> colors = {
    'الأكل': Colors.orange,
    'الشرب': Colors.blue,
    'النشاط': Colors.green,
    'الصحة النفسية': Colors.purple,
    'السمع': Colors.redAccent,
    'البصر': Colors.teal,
  };

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      backgroundColor: theme.scaffoldBackgroundColor, // استخدام لون الخلفية من الثيم
      appBar: AppBar(
        title: Text('مؤشرات الطفل الصحية'),
        // يتم تطبيق الألوان من الثيم
      ),
      body: LayoutBuilder(
        builder: (context, constraints) {
          double width = constraints.maxWidth;
          int crossAxisCount = width > 600 ? 3 : 2; // تخطيط للـ iPad

          return Column(
            children: [
              Expanded(
                child: GridView.builder(
                  padding: EdgeInsets.all(16),
                  itemCount: indicators.length,
                  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                    crossAxisCount: crossAxisCount,
                    crossAxisSpacing: 16,
                    mainAxisSpacing: 16,
                    childAspectRatio: 0.9, // نسبة عرض إلى ارتفاع لعناصر Grid
                  ),
                  itemBuilder: (context, index) {
                    String key = indicators.keys.elementAt(index);
                    return Card(
                      shape: RoundedRectangleBorder(
                        borderRadius: BorderRadius.circular(20),
                      ),
                      elevation: 6,
                      color: Colors.white,
                      child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          CircularPercentIndicator(
                            radius: 50.0,
                            lineWidth: 8.0,
                            percent: indicators[key]!,
                            center: Icon(
                              icons[key],
                              size: 36,
                              color: colors[key],
                            ),
                            progressColor: colors[key],
                            backgroundColor: Colors.grey[200]!,
                            animation: true,
                            animationDuration: 1000,
                          ),
                          SizedBox(height: 10),
                          Text(
                            key,
                            style: theme.textTheme.titleMedium?.copyWith(
                              color: colors[key],
                              fontWeight: FontWeight.bold,
                            ),
                          ),
                          Text(
                            '${(indicators[key]! * 100).toInt()}%',
                            style: theme.textTheme.bodyMedium?.copyWith(
                              color: Colors.black87,
                            ),
                          ),
                        ],
                      ),
                    );
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.symmetric(vertical: 16.0),
                child: ElevatedButton.icon(
                  onPressed: () {
                    ScaffoldMessenger.of(context).showSnackBar(
                      SnackBar(content: Text('ميزة تحليل الشخصية قريباً!')),
                    );
                  },
                  style: ElevatedButton.styleFrom(
                    backgroundColor: theme.colorScheme.secondary, // استخدام لون الثانوي من الثيم
                    foregroundColor: theme.colorScheme.onSecondary, // لون النص من الثيم
                    padding: EdgeInsets.symmetric(horizontal: 24, vertical: 12),
                    shape: RoundedRectangleBorder(
                      borderRadius: BorderRadius.circular(30),
                    ),
                  ),
                  icon: Icon(Icons.analytics, size: 24),
                  label: Text(
                    'تحليل شخصية الطفل',
                    style: theme.textTheme.labelLarge,
                  ),
                ),
              ),
            ],
          );
        },
      ),
    );
  }
}
```

#### `lib/screens/child_features/health_records_timeline_screen.dart`

```dart
import 'package:flutter/material.dart';

// 1. Enum لأنواع السجلات الصحية
enum HealthRecordType { vaccination, checkup, allergyNote, medication, generalNote }

// 2. كلاس لنموذج السجل الصحي
class HealthRecord {
  final DateTime date;
  final HealthRecordType type;
  final String details;
  final DateTime? nextDueDate;
  final String enteredBy;

  HealthRecord({
    required this.date,
    required this.type,
    required this.details,
    this.nextDueDate,
    required this.enteredBy,
  });
}

// 3. دالة مساعدة للحصول على معلومات (نص، أيقونة، لون) لكل نوع سجل
Map<String, dynamic> _getRecordTypeInfo(HealthRecordType type) {
  switch (type) {
    case HealthRecordType.vaccination:
      return {
        'text': 'تطعيم',
        'icon': Icons.vaccines_rounded,
        'color': Colors.teal[600]
      };
    case HealthRecordType.checkup:
      return {
        'text': 'فحص دوري',
        'icon': Icons.medical_information_rounded,
        'color': Colors.blue[600]
      };
    case HealthRecordType.allergyNote:
      return {
        'text': 'ملاحظة حساسية',
        'icon': Icons.warning_amber_rounded,
        'color': Colors.orange[700]
      };
    case HealthRecordType.medication:
      return {
        'text': 'دواء',
        'icon': Icons.medication_liquid_rounded,
        'color': Colors.purple[600]
      };
    case HealthRecordType.generalNote:
    default:
      return {
        'text': 'ملاحظة صحية',
        'icon': Icons.note_alt_rounded,
        'color': Colors.grey[600]
      };
  }
}

class HealthRecordsTimelineLeftTimeline extends StatelessWidget {
  HealthRecordsTimelineLeftTimeline({Key? key}) : super(key: key);

  // 4. بيانات تجريبية للسجلات الصحية
  final List<HealthRecord> healthRecords = [
    HealthRecord(
        date: DateTime(2025, 4, 29),
        type: HealthRecordType.vaccination,
        details: 'تم بنجاح تطعيم الكبد الوبائي ب. لا توجد أي أعراض جانبية مسجلة.',
        nextDueDate: null,
        enteredBy: 'Supervisor'),
    HealthRecord(
        date: DateTime(2023, 5, 15),
        type: HealthRecordType.vaccination,
        details:
            'لقاح الحصبة والنكاف والحصبة الألمانية (MMR) - الجرعة الأولى. تم إعطاؤه في العيادة.',
        nextDueDate: DateTime(2027, 5, 15),
        enteredBy: 'مدير النظام'),
    HealthRecord(
        date: DateTime(2024, 1, 10),
        type: HealthRecordType.checkup,
        details: 'فحص طبي عام - كل شيء طبيعي. تم قياس الطول والوزن وضغط الدم.',
        nextDueDate: DateTime(2025, 1, 10),
        enteredBy: 'طبيب المركز'),
    HealthRecord(
        date: DateTime(2024, 3, 20),
        type: HealthRecordType.allergyNote,
        details: 'حساسية من البنسلين تسبب طفح جلدي وحكة شديدة.',
        nextDueDate: null,
        enteredBy: 'ولي الأمر'),
    HealthRecord(
        date: DateTime(2023, 1, 5),
        type: HealthRecordType.medication,
        details: 'مضاد حيوي (أموكسيسيلين) لمدة 7 أيام بسبب التهاب في الأذن الوسطى.',
        nextDueDate: null,
        enteredBy: 'طبيب الأطفال'),
  ];

  // 5. دالة مساعدة لتنسيق التاريخ
  String _formatDate(DateTime? date) {
    if (date == null) return '-';
    return "${date.year}-${date.month.toString().padLeft(2, '0')}-${date.day.toString().padLeft(2, '0')}";
  }

  @override
  Widget build(BuildContext context) {
    final Color primaryColor = Theme.of(context).colorScheme.primary;

    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'السجلات الصحية',
          textAlign: TextAlign.right,
        ),
        centerTitle: true,
        backgroundColor: Theme.of(context).appBarTheme.backgroundColor, // استخدام لون الثيم
        foregroundColor: Theme.of(context).appBarTheme.foregroundColor, // استخدام لون الثيم
        elevation: 1.5,
        leading: Navigator.canPop(context)
            ? IconButton(
                icon: const Icon(Icons.arrow_back_ios, color: Colors.black54),
                onPressed: () => Navigator.pop(context),
              )
            : null,
      ),
      body: Directionality( // الحفاظ على RTL هنا
        textDirection: TextDirection.rtl,
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Padding(
              padding:
                  const EdgeInsetsDirectional.fromSTEB(16.0, 16.0, 16.0, 8.0),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceBetween,
                children: [
                  const Text(
                    'السجلات (الأحدث أولاً)',
                    style: TextStyle(
                      fontSize: 18,
                      fontWeight: FontWeight.bold,
                      color: Colors.black87,
                    ),
                    textAlign: TextAlign.right,
                  ),
                  OutlinedButton.icon(
                    icon: const Icon(Icons.edit_note, size: 18),
                    label: const Text('إدارة السجلات'),
                    onPressed: () {
                      // TODO: Implement navigation to manage records screen
                      ScaffoldMessenger.of(context).showSnackBar(
                        SnackBar(content: Text('إدارة السجلات غير متاحة بعد.')),
                      );
                    },
                    style: OutlinedButton.styleFrom(
                        foregroundColor: primaryColor,
                        side: BorderSide(color: primaryColor.withOpacity(0.5)),
                        padding: const EdgeInsets.symmetric(
                            horizontal: 12, vertical: 8),
                        textStyle: const TextStyle(
                            fontSize: 13, fontWeight: FontWeight.w600)),
                  ),
                ],
              ),
            ),
            Expanded(
              child: healthRecords.isEmpty
                  ? Center(
                      child: Text(
                        'لا توجد سجلات صحية لعرضها.',
                        style: TextStyle(
                            fontSize: 16, color: Colors.grey[600]),
                        textAlign: TextAlign.right,
                      ),
                    )
                  : ListView.builder(
                      itemCount: healthRecords.length,
                      padding: const EdgeInsets.symmetric(vertical: 10.0),
                      itemBuilder: (context, index) {
                        final record = healthRecords[index];
                        final bool isFirst = index == 0;
                        final bool isLast = index == healthRecords.length - 1;
                        return Padding(
                          padding: const EdgeInsets.only(bottom: 20.0),
                          child:
                              _buildTimelineTileLeftTimelineRightContent(
                                  context, record, isFirst, isLast),
                        );
                      },
                    ),
            ),
          ],
        ),
      ),
      backgroundColor: Colors.grey[100], // استخدام لون خلفية ثابت
    );
  }

  // 6. ودجت لبناء عنصر المخطط الزمني
  Widget _buildTimelineTileLeftTimelineRightContent(BuildContext context,
      HealthRecord record, bool isFirst, bool isLast) {
    final typeInfo = _getRecordTypeInfo(record.type);
    final Color timelineColor = typeInfo['color'] ?? Colors.grey;
    final IconData timelineIcon = typeInfo['icon'] ?? Icons.circle;

    const double iconBackgroundRadius = 18.0;
    const double iconSize = 20.0;
    const double lineWidth = 2.0;

    return IntrinsicHeight(
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Padding(
            padding: const EdgeInsetsDirectional.only(start: 16.0),
            child: SizedBox(
              width: iconBackgroundRadius * 2,
              child: Column(
                mainAxisSize: MainAxisSize.max,
                children: [
                  Container(
                    width: lineWidth,
                    height: 15.0,
                    color: isFirst ? Colors.transparent : Colors.grey[300],
                  ),
                  CircleAvatar(
                    radius: iconBackgroundRadius,
                    backgroundColor: timelineColor.withOpacity(0.95),
                    child: Icon(timelineIcon,
                        size: iconSize, color: Colors.white),
                  ),
                  Expanded(
                    child: Container(
                      width: lineWidth,
                      color: isLast ? Colors.transparent : Colors.grey[300],
                    ),
                  ),
                ],
              ),
            ),
          ),
          Expanded(
            child: Padding(
              padding: const EdgeInsetsDirectional.only(
                  start: 16.0, end: 20.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                mainAxisSize: MainAxisSize.min,
                children: [
                  Text(
                    _formatDate(record.date),
                    style: TextStyle(
                        fontSize: 20,
                        color: Colors.grey[800],
                        fontWeight: FontWeight.w600),
                    textAlign: TextAlign.right,
                  ),
                  const SizedBox(height: 8),
                  Text(
                    record.details,
                    style: const TextStyle(
                        fontSize: 16, color: Colors.black87, height: 1.45),
                    textAlign: TextAlign.right,
                  ),
                  if (record.nextDueDate != null) ...[
                    const SizedBox(height: 10),
                    Row(
                      mainAxisAlignment: MainAxisAlignment.start,
                      children: [
                        Icon(Icons.event_repeat_rounded,
                            size: 15, color: Colors.red[800]),
                        const SizedBox(width: 5),
                        Text(
                          'الاستحقاق القادم: ${_formatDate(record.nextDueDate)}',
                          style: TextStyle(
                              fontSize: 13,
                              color: Colors.red[800],
                              fontWeight: FontWeight.w500),
                          textAlign: TextAlign.right,
                        ),
                      ],
                    ),
                  ],
                  const SizedBox(height: 10),
                  Text(
                    'أُدخل بواسطة: ${record.enteredBy}',
                    style: TextStyle(
                        fontSize: 12, color: Colors.grey[600]),
                    textAlign: TextAlign.right,
                  ),
                ],
              ),
            ),
          ),
        ],
      ),
    );
  }
}
```

#### `lib/screens/child_features/daily_meal_record_page.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';

class DailyMealRecordPage extends StatelessWidget {
  final List<Map<String, String>> mealRecords = const [
    {
      'date': '2025-04-29',
      'meal': 'زيت وزعتر سندويش',
      'status': 'أكل جيدًا',
      'notes': 'لا ملاحظات',
      'details': 'سندويش خبز أسمر مع زيت زيتون أصلي وزعتر طازج.',
    },
    {
      'date': '2025-04-28',
      'meal': 'جبنة سندويش',
      'status': 'أكل جيدًا',
      'notes': 'طلب المزيد',
      'details': 'سندويش خبز أبيض مع شرائح جبنة شيدر.',
    },
    {
      'date': '2025-04-27',
      'meal': 'بيض مسلوق',
      'status': 'لم يأكل',
      'notes': 'لم يرغب بالأكل',
      'details': 'بيضتان مسلوقتان جيدًا.',
    },
    {
      'date': '2025-04-26',
      'meal': 'فواكه مشكلة',
      'status': 'أكل قليلاً',
      'notes': 'كان يفضل الموز فقط',
      'details': 'تشكيلة من التفاح المقطع، العنب، وشرائح الموز.',
    },
  ];

  Color _getStatusColor(String status) {
    switch (status) {
      case 'أكل جيدًا':
        return Colors.green.shade600;
      case 'أكل قليلاً':
        return Colors.orange.shade600;
      case 'لم يأكل':
        return Colors.red.shade600;
      default:
        return Colors.grey.shade600;
    }
  }

  String _formatDate(String dateStr) {
    try {
      final dateTime = DateTime.parse(dateStr);
      return DateFormat('dd-MM-yyyy').format(dateTime);
    } catch (e) {
      return dateStr;
    }
  }

  void _showMealDetails(BuildContext context, Map<String, String> record) {
    showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          title: Text('تفاصيل وجبة ${record['meal']}', textAlign: TextAlign.right),
          content: Column(
            crossAxisAlignment: CrossAxisAlignment.end,
            mainAxisSize: MainAxisSize.min,
            children: [
              Text('التاريخ: ${_formatDate(record['date'] ?? '')}', textAlign: TextAlign.right),
              const SizedBox(height: 8),
              Text('الحالة: ${record['status']}', textAlign: TextAlign.right),
              const SizedBox(height: 8),
              Text('ملاحظات: ${record['notes']}', textAlign: TextAlign.right),
              const SizedBox(height: 16),
              Text(
                'التفاصيل:',
                style: TextStyle(fontWeight: FontWeight.bold),
                textAlign: TextAlign.right,
              ),
              Text(record['details'] ?? 'لا توجد تفاصيل.', textAlign: TextAlign.right),
            ],
          ),
          actions: <Widget>[
            TextButton(
              child: const Text('إغلاق'),
              onPressed: () {
                Navigator.of(context).pop();
              },
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        // تم استخدام ألوان الثيم للـ AppBar
        title: const Text(
          'سجل وجبات الطالب',
          style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
        ),
        centerTitle: true,
        elevation: 1,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Container(
              padding: const EdgeInsets.symmetric(vertical: 12, horizontal: 16),
              decoration: BoxDecoration(
                color: theme.colorScheme.primary.withOpacity(0.1), // لون من الثيم
                borderRadius: BorderRadius.circular(12),
              ),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceBetween,
                children: [
                  Text(
                    'اسم الطفل',
                    style: theme.textTheme.titleMedium?.copyWith(fontWeight: FontWeight.w500),
                  ),
                  Text(
                    'زينب حسن', // يمكنك استبدال هذا ببيانات فعلية من الطفل
                    style: theme.textTheme.titleMedium,
                  ),
                ],
              ),
            ),
            const SizedBox(height: 20),
            Text(
              'سجل الوجبات الأخير',
              style: theme.textTheme.headlineSmall?.copyWith(
                color: Colors.grey.shade800,
              ),
            ),
            const SizedBox(height: 12),
            Expanded(
              child: ListView.builder(
                itemCount: mealRecords.length,
                itemBuilder: (context, index) {
                  final record = mealRecords[index];
                  return GestureDetector(
                    onTap: () {
                      _showMealDetails(context, record);
                    },
                    child: Card(
                      elevation: 3,
                      margin: const EdgeInsets.only(bottom: 16),
                      shape: RoundedRectangleBorder(
                        borderRadius: BorderRadius.circular(10),
                      ),
                      child: Padding(
                        padding: const EdgeInsets.all(16.0),
                        child: Column(
                          crossAxisAlignment: CrossAxisAlignment.start,
                          children: [
                            Row(
                              mainAxisAlignment: MainAxisAlignment.spaceBetween,
                              children: [
                                Text(
                                  'التاريخ: ${_formatDate(record['date'] ?? '')}',
                                  style: theme.textTheme.bodyLarge?.copyWith(
                                      fontWeight: FontWeight.w500),
                                ),
                                Text(
                                  'الوجبة: ${record['meal']}',
                                  style: theme.textTheme.bodyLarge,
                                ),
                              ],
                            ),
                            const SizedBox(height: 10),
                            Row(
                              mainAxisAlignment: MainAxisAlignment.spaceBetween,
                              children: [
                                Row(
                                  children: [
                                    Icon(
                                      Icons.circle,
                                      size: 14,
                                      color: _getStatusColor(
                                          record['status'] ?? ''),
                                    ),
                                    const SizedBox(width: 10),
                                    Text(
                                      'الحالة: ${record['status']}',
                                      style: theme.textTheme.bodyLarge?.copyWith(
                                        color: _getStatusColor(
                                            record['status'] ?? ''),
                                        fontWeight: FontWeight.bold,
                                      ),
                                    ),
                                  ],
                                ),
                                const SizedBox(width: 66),
                                Expanded(
                                  child: Text(
                                    'ملاحظات: ${record['notes']}',
                                    style: theme.textTheme.bodyLarge,
                                    textAlign: TextAlign.end,
                                    overflow: TextOverflow.ellipsis,
                                  ),
                                ),
                              ],
                            ),
                          ],
                        ),
                      ),
                    ),
                  );
                },
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

#### `lib/screens/child_features/student_activity_schedule_page.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart'; // لعرض أسماء الأيام والتوقيت

// --- 1. نموذج بيانات للنشاط ---
class Activity {
  final String id;
  final int dayOfWeek; // 1: Monday, ..., 7: Sunday
  final TimeOfDay startTime;
  final TimeOfDay? endTime;
  final String name; // اسم النشاط
  final IconData icon;
  final Color? color;
  final String? location;

  Activity({
    required this.id,
    required this.dayOfWeek,
    required this.startTime,
    this.endTime,
    required this.name, // مطلوب الآن
    required this.icon,
    this.color,
    this.location,
  });
}

// --- 2. شاشة عرض جدول الأنشطة ---
class StudentActivitySchedulePage extends StatefulWidget {
  const StudentActivitySchedulePage({Key? key}) : super(key: key);

  @override
  _StudentActivitySchedulePageState createState() => _StudentActivitySchedulePageState();
}

class _StudentActivitySchedulePageState extends State<StudentActivitySchedulePage> {

  // --- 3. بيانات وهمية للأنشطة (مع أسماء عربية) ---
  final List<Activity> weeklyActivities = [
    // الاثنين
    Activity(id: 'a1', dayOfWeek: DateTime.monday, startTime: TimeOfDay(hour: 8, minute: 30), name: 'لعبة تركيب الصور (Puzzle)', icon: Icons.extension_outlined, color: Colors.orange[300]),
    Activity(id: 'a2', dayOfWeek: DateTime.monday, startTime: TimeOfDay(hour: 9, minute: 30), name: 'وقت القصة', icon: Icons.menu_book_outlined, color: Colors.blue[300]),
    Activity(id: 'a3', dayOfWeek: DateTime.monday, startTime: TimeOfDay(hour: 10, minute: 30), name: 'اللعب الحر في الساحة', icon: Icons.directions_run_outlined, location: 'الساحة الخارجية'),
    Activity(id: 'a4', dayOfWeek: DateTime.monday, startTime: TimeOfDay(hour: 11, minute: 30), name: 'وجبة خفيفة', icon: Icons.restaurant_menu),

    // الثلاثاء
    Activity(id: 'a5', dayOfWeek: DateTime.tuesday, startTime: TimeOfDay(hour: 8, minute: 30), name: 'نشاط فني: رسم وتلوين', icon: Icons.palette_outlined, color: Colors.pink[300]),
    Activity(id: 'a6', dayOfWeek: DateTime.tuesday, startTime: TimeOfDay(hour: 9, minute: 30), name: 'أغاني وأناشيد', icon: Icons.music_note_outlined, color: Colors.purple[300]),
    Activity(id: 'a7', dayOfWeek: DateTime.tuesday, startTime: TimeOfDay(hour: 10, minute: 30), name: 'تمارين رياضية خفيفة', icon: Icons.fitness_center_outlined),
     Activity(id: 'a8', dayOfWeek: DateTime.tuesday, startTime: TimeOfDay(hour: 11, minute: 30), name: 'وجبة خفيفة', icon: Icons.restaurant_menu),

    // الأربعاء
     Activity(id: 'a9', dayOfWeek: DateTime.wednesday, startTime: TimeOfDay(hour: 9, minute: 00), name: 'مقدمة عن الحروف', icon: Icons.abc_outlined, color: Colors.green[400]),
     Activity(id: 'a10', dayOfWeek: DateTime.wednesday, startTime: TimeOfDay(hour: 10, minute: 00), name: 'اللعب بالمعجون', icon: Icons.grain_outlined, color: Colors.brown[300]),
     Activity(id: 'a11', dayOfWeek: DateTime.wednesday, startTime: TimeOfDay(hour: 11, minute: 00), name: 'اللعب الحر في الداخل', icon: Icons.toys_outlined, location: 'غرفة الألعاب'),

    // الخميس
    Activity(id: 'a12', dayOfWeek: DateTime.thursday, startTime: TimeOfDay(hour: 8, minute: 30), name: 'مراجعة الألوان والأشكال', icon: Icons.interests_outlined, color: Colors.red[300]),
    Activity(id: 'a13', dayOfWeek: DateTime.thursday, startTime: TimeOfDay(hour: 9, minute: 30), name: 'نشاط رياضي جماعي', icon: Icons.sports_soccer_outlined, color: Colors.lightBlue[400], location: 'الساحة الرياضية'),
     Activity(id: 'a14', dayOfWeek: DateTime.thursday, startTime: TimeOfDay(hour: 11, minute: 00), name: 'وجبة خفيفة ونهاية اليوم', icon: Icons.celebration_outlined),

    // الجمعة، السبت (لا توجد أنشطة هنا)
  ];

  // --- 4. تجميع الأنشطة حسب اليوم ---
  Map<int, List<Activity>> _groupActivitiesByDay() {
     final Map<int, List<Activity>> groupedActivities = {};
    for (var activity in weeklyActivities) {
      if (groupedActivities[activity.dayOfWeek] == null) groupedActivities[activity.dayOfWeek] = [];
      groupedActivities[activity.dayOfWeek]!.add(activity);
    }
    groupedActivities.forEach((day, activities) {
      activities.sort((a, b) {
        double aTime = a.startTime.hour + a.startTime.minute / 60.0;
        double bTime = b.startTime.hour + b.startTime.minute / 60.0;
        return aTime.compareTo(bTime);
      });
    });
    return groupedActivities;
  }

  // --- 5. دالة مساعدة للحصول على اسم اليوم (RTL Example - Arabic Name) ---
  String _getDayName(int dayOfWeek, BuildContext context) {
    DateTime now = DateTime.now();
    // الحصول على أول يوم من الأسبوع (الاثنين) لهذه السنة
    DateTime firstDayOfWeek = now.subtract(Duration(days: now.weekday - DateTime.monday));
    // الحصول على اليوم المستهدف من خلال إضافة الأيام
    DateTime targetDay = firstDayOfWeek.add(Duration(days: dayOfWeek - DateTime.monday));
    return DateFormat('EEEE', 'ar').format(targetDay); // اسم اليوم بالعربية
  }


  // --- 6. دالة مساعدة لتنسيق الوقت (RTL Example) ---
  String _formatTimeOfDay(TimeOfDay time, BuildContext context) {
    final localizations = MaterialLocalizations.of(context);
    // for LTR `alwaysUse24HourFormat: false` might render AM/PM differently
    return localizations.formatTimeOfDay(time, alwaysUse24HourFormat: false);
  }

  @override
  Widget build(BuildContext context) {
    final groupedActivities = _groupActivitiesByDay();
    // عرض الأيام بترتيب الأحد إلى الخميس في الـ RTL
    final displayOrder = [
      DateTime.sunday, // الأحد أولًا في الترتيب العربي التقليدي
      DateTime.monday,
      DateTime.tuesday,
      DateTime.wednesday,
      DateTime.thursday,
    ];

    final theme = Theme.of(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('جدول الأنشطة الأسبوعي'), // عنوان بالعربية
        centerTitle: true,
        // يمكنك إزالة flexibleSpace لتترك لون AppBar للـ theme
        // flexibleSpace: Container(
        //   decoration: BoxDecoration(
        //     gradient: LinearGradient(
        //       colors: [theme.colorScheme.primary, theme.colorScheme.primary],
        //       begin: Alignment.topLeft,
        //       end: Alignment.bottomRight,
        //     ),
        //   ),
        // ),
        // يستخدم الـ elevation من الثيم
      ),
      body: ListView.builder(
        padding: EdgeInsets.symmetric(vertical: 8.0, horizontal: 12.0),
        itemCount: displayOrder.length,
        itemBuilder: (context, index) {
          final day = displayOrder[index];
          final activitiesForDay = groupedActivities[day] ?? [];

          // --- 7. بناء قسم لكل يوم ---
          return _buildDaySection(context, theme, day, activitiesForDay);
        },
      ),
    );
  }

  // --- 8. ودجت بناء قسم اليوم ---
  Widget _buildDaySection(BuildContext context, ThemeData theme, int dayOfWeek, List<Activity> activities) {
    return Card(
      margin: EdgeInsets.only(bottom: 16.0),
      elevation: 3.0,
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12.0)),
      child: Padding(
        padding: const EdgeInsets.all(12.0),
        child: Column(
          // في RTL، crossAxisAlignment.start تعني محاذاة لليمين
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // -- Day Header --
            Text(
              _getDayName(dayOfWeek, context), // اسم اليوم بالعربية
              style: theme.textTheme.headlineSmall?.copyWith(
                color: theme.colorScheme.primary, // استخدم لون أساسي من الثيم
                fontWeight: FontWeight.bold,
              ),
            ),
            Divider(thickness: 1.0, height: 20.0),

            // -- List of Activities for the day --
            if (activities.isEmpty)
              Padding(
                padding: const EdgeInsets.symmetric(vertical: 16.0),
                child: Center(
                  child: Text(
                    'لا توجد أنشطة مجدولة لهذا اليوم.', // نص عربي
                    style: TextStyle(color: Colors.grey.shade600, fontStyle: FontStyle.italic),
                  ),
                ),
              )
            else
              ListView.separated(
                shrinkWrap: true,
                physics: NeverScrollableScrollPhysics(),
                itemCount: activities.length,
                itemBuilder: (context, activityIndex) {
                  final activity = activities[activityIndex];
                  return Padding(
                    padding: const EdgeInsets.symmetric(vertical: 8.0),
                    child: _buildActivityTile(context, theme, activity),
                  );
                },
                separatorBuilder: (context, index) => Divider(height: 1, thickness: 0.5, indent: 50, endIndent: 10),
              ),
          ],
        ),
      ),
    );
  }

  // --- 9. ودجت بناء عنصر النشاط ---
  Widget _buildActivityTile(BuildContext context, ThemeData theme, Activity activity) {
    return ListTile(
      contentPadding: EdgeInsets.zero, // إزالة التباعد الداخلي الافتراضي
      leading: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.center, // توسيط عمودي في العمود
        children: [
          Text(
            _formatTimeOfDay(activity.startTime, context),
            style: theme.textTheme.titleSmall?.copyWith(
              fontWeight: FontWeight.bold,
              color: activity.color ?? theme.colorScheme.primary,
            ),
          ),
           SizedBox(height: 4),
           Icon(activity.icon, color: activity.color ?? theme.colorScheme.secondary, size: 26),
        ],
      ),
      title: Text(
        activity.name,
        style: theme.textTheme.bodyLarge?.copyWith(fontWeight: FontWeight.w500),
        textAlign: TextAlign.start, // يبدأ من اليمين في RTL
      ),
      subtitle: activity.location != null
          ? Row(
              // في RTL، Row يرتب العناصر من اليمين لليسار.
              // إذا أردت الأيقونة ثم النص (من اليسار لليمين داخل السطر الواحد)، استخدم Directionality
              children: [
                Icon(Icons.location_on_outlined, size: 14, color: Colors.grey.shade600),
                SizedBox(width: 4),
                Expanded( // استخدم Expanded لضمان أن النص لا يتجاوز
                  child: Text(activity.location!, style: TextStyle(color: Colors.grey.shade600, fontSize: 12),
                  textAlign: TextAlign.start, // يبدأ من اليمين في RTL
                  ),
                ),
              ],
            )
          : null,
       dense: false,
    );
  }
}
```

#### `lib/screens/child_features/student_media_gallery_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart'; // لعرض التاريخ بتنسيق سهل القراءة

// --- 1. نموذج بيانات للوسائط ---
enum MediaType { image, video }

class MediaItem {
  final String id;
  final MediaType type;
  final String thumbnailUrl;
  final String fullUrl;
  final DateTime timestamp;
  final String? caption;
  final String? studentName;

  MediaItem({
    required this.id,
    required this.type,
    required this.thumbnailUrl,
    required this.fullUrl,
    required this.timestamp,
    this.caption,
    this.studentName,
  });
}

// --- 2. شاشة عرض الوسائط ---
class StudentMediaGalleryScreen extends StatefulWidget {
  const StudentMediaGalleryScreen({Key? key}) : super(key: key);

  @override
  _StudentMediaGalleryScreenState createState() => _StudentMediaGalleryScreenState();
}

class _StudentMediaGalleryScreenState extends State<StudentMediaGalleryScreen> {

  // --- 3. بيانات وهمية (استبدلها ببيانات فعلية) ---
  final List<MediaItem> allMediaItems = [
     MediaItem(id: 'm1', type: MediaType.image, thumbnailUrl: 'assets/1.png', fullUrl: 'assets/1.png', timestamp: DateTime.now().subtract(Duration(hours: 1)), caption: 'زينب ترسم وردة', studentName: 'زينب حسن'),
    MediaItem(id: 'm2', type: MediaType.video, thumbnailUrl: 'assets/2.png', fullUrl: 'VIDEO_URL_1', timestamp: DateTime.now().subtract(Duration(hours: 2)), caption: 'وقت اللعب في الساحة'),
    MediaItem(id: 'm3', type: MediaType.image, thumbnailUrl: 'assets/3.png', fullUrl: 'assets/3.png', timestamp: DateTime.now().subtract(Duration(hours: 3)), caption: 'وقت القصة'),
    MediaItem(id: 'm4', type: MediaType.image, thumbnailUrl: 'assets/1.png', fullUrl: 'assets/1.png', timestamp: DateTime.now().subtract(Duration(days: 1, hours: 5)), studentName: 'أحمد علي'),
    MediaItem(id: 'm5', type: MediaType.video, thumbnailUrl: 'assets/2.png', fullUrl: 'VIDEO_URL_2', timestamp: DateTime.now().subtract(Duration(days: 1, hours: 6)), caption: 'أغنية الصباح'),
    MediaItem(id: 'm6', type: MediaType.image, thumbnailUrl: 'assets/3.png', fullUrl: 'assets/3.png', timestamp: DateTime.now().subtract(Duration(days: 1, hours: 7)), caption: 'مشروع فني'),
    MediaItem(id: 'm7', type: MediaType.image, thumbnailUrl: 'assets/1.png', fullUrl: 'assets/1.png', timestamp: DateTime.now().subtract(Duration(days: 2, hours: 1)), caption: 'صورة جماعية'),
 ];

  // --- 4. تجميع الوسائط حسب التاريخ ---
  Map<DateTime, List<MediaItem>> _groupMediaByDate() {
     final Map<DateTime, List<MediaItem>> groupedMedia = {};
    for (var item in allMediaItems) {
      final dateKey = DateTime(item.timestamp.year, item.timestamp.month, item.timestamp.day);
      if (groupedMedia[dateKey] == null) {
        groupedMedia[dateKey] = [];
      }
      groupedMedia[dateKey]!.add(item);
    }
     final sortedKeys = groupedMedia.keys.toList()..sort((a, b) => b.compareTo(a));
     final Map<DateTime, List<MediaItem>> sortedGroupedMedia = { for (var key in sortedKeys) key: groupedMedia[key]! };
     return sortedGroupedMedia;
  }

  // --- 5. دالة مساعدة لتنسيق التاريخ (RTL Example) ---
  String _formatDateHeader(DateTime date) {
    final now = DateTime.now();
    final today = DateTime(now.year, now.month, now.day);
    final yesterday = today.subtract(Duration(days: 1));

    if (date == today) return 'اليوم'; // Today in Arabic
    if (date == yesterday) return 'أمس'; // Yesterday in Arabic
    // Use Arabic format for other dates
    return DateFormat('EEEE, d MMMM yyyy', 'ar').format(date);
  }

  @override
  Widget build(BuildContext context) {
    final groupedMedia = _groupMediaByDate();
    final dates = groupedMedia.keys.toList();
    final theme = Theme.of(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('الوسائط اليومية'),
        elevation: 1.0,
      ),
      body: groupedMedia.isEmpty
          ? Center(child: Text('لا توجد وسائط لعرضها حالياً.'))
          : ListView.builder(
              padding: EdgeInsets.all(8.0),
              itemCount: dates.length,
              itemBuilder: (context, index) {
                final date = dates[index];
                final itemsForDate = groupedMedia[date]!;

                return Column(
                  // Align text to the right in RTL
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    // -- Date Header --
                    Padding(
                      padding: const EdgeInsets.symmetric(vertical: 12.0, horizontal: 8.0),
                      child: Text(
                        _formatDateHeader(date),
                        style: theme.textTheme.titleMedium?.copyWith(
                          fontWeight: FontWeight.bold,
                          color: theme.colorScheme.primary,
                        ),
                         textAlign: TextAlign.start, // align to right in RTL
                      ),
                    ),
                    // -- Media Grid for this date --
                    GridView.builder(
                      shrinkWrap: true,
                      physics: NeverScrollableScrollPhysics(),
                      gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                        crossAxisCount: 3,
                        crossAxisSpacing: 6.0,
                        mainAxisSpacing: 6.0,
                      ),
                      itemCount: itemsForDate.length,
                      itemBuilder: (context, gridIndex) {
                        final item = itemsForDate[gridIndex];
                        return _buildMediaGridItem(context, item);
                      },
                    ),
                    SizedBox(height: 16),
                  ],
                );
              },
            ),
    );
  }

  // --- 7. ودجت بناء عنصر الشبكة ---
  Widget _buildMediaGridItem(BuildContext context, MediaItem item) {
    return InkWell(
      onTap: () {
        if (item.type == MediaType.image) {
          Navigator.push(context, MaterialPageRoute(builder: (context) => FullScreenImageViewer(imageUrl: item.fullUrl)));
        } else if (item.type == MediaType.video) {
          // TODO: Implement navigation to VideoPlayerScreen (requires a video player package)
          ScaffoldMessenger.of(context).showSnackBar(
            SnackBar(content: Text('تشغيل الفيديو (${item.fullUrl}) غير متاح بعد.')),
          );
        }
      },
      child: Card(
        elevation: 2.0,
        clipBehavior: Clip.antiAlias,
        shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(8.0)),
        child: Stack(
          fit: StackFit.expand,
          children: [
            // -- Thumbnail Image --
            Image.asset( // Changed to Image.asset for local assets
              item.thumbnailUrl,
              fit: BoxFit.cover,
              errorBuilder: (context, error, stackTrace) {
                 print("Error loading image asset: $error");
                 return Container(
                   color: Colors.grey[200],
                   child: Icon(Icons.broken_image_outlined, color: Colors.grey[400], size: 40),
                 );
               },
            ),

            // -- Video Icon Overlay --
            if (item.type == MediaType.video)
              Center(
                child: Container(
                   padding: EdgeInsets.all(6),
                   decoration: BoxDecoration(
                     color: Colors.black.withOpacity(0.5),
                     shape: BoxShape.circle,
                   ),
                   child: Icon(
                     Icons.play_arrow_rounded,
                     color: Colors.white,
                     size: 30.0,
                   ),
                 ),
              ),

            // -- Optional Caption/Name Overlay --
            if (item.caption != null || item.studentName != null)
              Positioned(
                 bottom: 0,
                 left: 0,
                 right: 0,
                 child: Container(
                   padding: EdgeInsets.symmetric(horizontal: 4.0, vertical: 2.0),
                   decoration: BoxDecoration(
                     gradient: LinearGradient(
                       begin: Alignment.bottomCenter,
                       end: Alignment.topCenter,
                       colors: [Colors.black.withOpacity(0.7), Colors.transparent],
                     ),
                   ),
                   child: Text(
                     item.caption ?? item.studentName ?? '',
                     style: TextStyle(color: Colors.white, fontSize: 10),
                     maxLines: 1,
                     overflow: TextOverflow.ellipsis,
                     textAlign: TextAlign.start, // align to right in RTL
                   ),
                 ),
               ),
          ],
        ),
      ),
    );
  }
}

// --- Optional Full Screen Viewer Widgets (simple implementation) ---

class FullScreenImageViewer extends StatelessWidget {
  final String imageUrl;
  const FullScreenImageViewer({Key? key, required this.imageUrl}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
      appBar: AppBar(
        backgroundColor: Colors.transparent,
        elevation: 0,
        iconTheme: IconThemeData(color: Colors.white),
      ),
      body: Center(
        child: Hero(
          tag: imageUrl, // Tag for Hero animation
          child: Image.asset( // Changed to Image.asset
            imageUrl,
            fit: BoxFit.contain,
            errorBuilder: (context, error, stackTrace) {
              return Icon(Icons.broken_image, color: Colors.white, size: 100);
            },
          ),
        ),
      ),
    );
  }
}

/*
class VideoPlayerScreen extends StatefulWidget {
  final String videoUrl;
  const VideoPlayerScreen({Key? key, required this.videoUrl}) : super(key: key);

  @override
  State<VideoPlayerScreen> createState() => _VideoPlayerScreenState();
}

class _VideoPlayerScreenState extends State<VideoPlayerScreen> {
  // Add video player initialization and dispose logic here
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Video Player')),
      body: Center(child: Text('Video player for ${widget.videoUrl}')),
    );
  }
}
*/
```

#### `lib/screens/child_features/educational_resources_list_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:url_launcher/url_launcher.dart';
// لإصلاحمشكلة  error for  MaterialLocalizations.of(context).formatDecimal and Localizations
// import 'package:flutter_localizations/flutter_localizations.dart';


//============================================================
// 1. Data Model and Sample Data (مدمجة هنا لتوضيح بسيط)
//============================================================

class EducationalResourceModel {
  final int id;
  final String title;
  final String description;
  final String type; // "رابط", "فيديو", etc.
  final String url;
  final String targetAge;
  final String subject;
  final String addedBy;
  final String dateAdded;

  EducationalResourceModel({
    required this.id,
    required this.title,
    this.description = '',
    required this.type,
    required this.url,
    required this.targetAge,
    required this.subject,
    required this.addedBy,
    required this.dateAdded,
  });
}

// بيانات تجريبية مطابقة للصورة
final List<EducationalResourceModel> sampleResources = [
  EducationalResourceModel(
    id: 1,
    title: 'كتاب اللغة الانكليزية',
    type: 'رابط',
    url: 'https://telegram.me/telegram_channel_or_link', // استبدل برابط فعلي
    targetAge: 'حتى 6',
    subject: '-',
    addedBy: 'مدير النظام',
    dateAdded: '2025-04-29',
  ),
  EducationalResourceModel(
    id: 2,
    title: 'أغنية الحروف الأبجدية',
    description: 'فيديو تعليمي ممتع لتعلم الحروف العربية',
    type: 'فيديو',
    url: 'https://www.youtube.com/watch?v=sW-d2E42b6Y', // استبدل برابط فعلي
    targetAge: '3 - 6',
    subject: 'اللغة العربية',
    addedBy: 'مدير النظام',
    dateAdded: '2025-04-27',
  ),
  EducationalResourceModel(
    id: 3,
    title: 'تعلم الأشكال الهندسية',
    description: 'نشاط تفاعلي لتعريف الأطفال بالأشكال الأساسية',
    type: 'رابط',
    url: 'http://kids.example.com/shapes_game', // استبدل برابط فعلي
    targetAge: '2 - 5',
    subject: 'الرياضيات',
    addedBy: 'مدير النظام',
    dateAdded: '2025-04-27',
  ),
];


//============================================================
// 2. Resource List Screen Widget (EducationalResourcesListScreen)
//============================================================

class EducationalResourcesListScreen extends StatelessWidget {
  final List<EducationalResourceModel> resources = sampleResources;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('قائمة المصادر التعليمية'),
        centerTitle: true,
      ),
      body: ListView.builder(
        padding: const EdgeInsets.all(8.0),
        itemCount: resources.length,
        itemBuilder: (context, index) {
          final resource = resources[index];
          return ResourceListItem(resource: resource);
        },
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          // TODO: Implement navigation to add new resource screen if needed
          ScaffoldMessenger.of(context).showSnackBar(
            const SnackBar(content: Text('شاشة إضافة مصدر جديد غير متاحة حالياً.')),
          );
        },
        child: const Icon(Icons.add),
        tooltip: 'إضافة مصدر جديد',
        backgroundColor: Theme.of(context).appBarTheme.backgroundColor,
      ),
    );
  }
}


//============================================================
// 3. Resource List Item Widget (ResourceListItem)
//============================================================

class ResourceListItem extends StatelessWidget {
  final EducationalResourceModel resource;

  const ResourceListItem({Key? key, required this.resource}) : super(key: key);

  // --- Helper Functions ---

  Future<void> _launchURL(BuildContext context, String urlString) async {
    // يجب أن تكون الـ URL صالحة لكي يتم إطلاقها
    final Uri? url = Uri.tryParse(urlString);
    if (url != null && await canLaunchUrl(url)) {
      try {
        await launchUrl(url, mode: LaunchMode.externalApplication);
      } catch (e) {
         ScaffoldMessenger.of(context).showSnackBar(
           SnackBar(content: Text('خطأ في فتح الرابط: $e')),
         );
      }
    } else {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('لا يمكن فتح الرابط: $urlString')),
      );
    }
  }


  Widget _buildTypeBadge(BuildContext context, String type) {
    Color badgeColor;
    String badgeText = type;

    switch (type.toLowerCase()) {
      case 'رابط':
        badgeColor = Colors.blue.shade600;
        break;
      case 'فيديو':
        badgeColor = Colors.red.shade600;
        break;
      case 'ملف':
        badgeColor = Colors.green.shade600;
        break;
      default:
        badgeColor = Colors.grey.shade600;
    }

    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 8, vertical: 3),
      decoration: BoxDecoration(
        color: badgeColor,
        borderRadius: BorderRadius.circular(12),
      ),
      child: Text(
        badgeText,
        style: const TextStyle(color: Colors.white, fontSize: 11, fontWeight: FontWeight.bold),
      ),
    );
  }

  Widget _buildInfoChip(BuildContext context, IconData icon, String label, String value, {bool isLink = false}) {
    Widget valueWidget = Text(
      value,
      style: TextStyle(
        color: isLink ? Colors.blue.shade700 : Colors.black87,
        fontSize: 13,
        overflow: TextOverflow.ellipsis,
      ),
      maxLines: 1,
    );

    if (isLink) {
      valueWidget = Flexible( // استخدام Flexible داخل Chip لمنع التجاوز
        child: InkWell(
          onTap: () => _launchURL(context, value),
          child: valueWidget,
        ),
      );
    } else {
       valueWidget = Flexible(child: valueWidget);
    }

    return Chip(
      avatar: Icon(icon, size: 16, color: Colors.grey.shade700),
      label: Row(
          mainAxisSize: MainAxisSize.min, // ضروري لـ Chip داخل Wrap
          children: [
            Text(
              '$label: ',
              style: TextStyle(fontSize: 13, color: Colors.grey.shade800, fontWeight: FontWeight.w500),
            ),
            valueWidget,
          ],
        ),
      backgroundColor: Colors.grey.shade200,
      padding: const EdgeInsets.symmetric(horizontal: 6, vertical: 2),
      materialTapTargetSize: MaterialTapTargetSize.shrinkWrap,
      visualDensity: VisualDensity.compact,
    );
 }

 // --- Build Method for the List Item ---

  @override
  Widget build(BuildContext context) {
    final textTheme = Theme.of(context).textTheme;
    final colorScheme = Theme.of(context).colorScheme;

    return Card(
      // استخدام theme cardTheme
      child: Padding(
        padding: const EdgeInsets.all(12.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // --- الصف الأول: العنوان والنوع ---
            Row(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                // --- الرقم التسلسلي والعنوان والوصف ---
                Expanded(
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Row(
                        crossAxisAlignment: CrossAxisAlignment.start, // محاذاة البداية للرقم والعنوان
                        children: [
                          Padding(
                            padding: const EdgeInsets.only(top: 2.0), // لضبط محاذاة الرقم رأسياً
                            child: Text(
                              '${resource.id}. ',
                              style: textTheme.titleMedium?.copyWith(fontWeight: FontWeight.bold),
                            ),
                          ),
                          Expanded(
                            child: InkWell(
                                onTap: () => _launchURL(context, resource.url),
                                child: Text(
                                  resource.title,
                                  style: textTheme.titleMedium?.copyWith(
                                    fontWeight: FontWeight.bold,
                                    color: colorScheme.primary, // لون مميز للرابط
                                    height: 1.3, // تحسين تباعد الأسطر إذا التف النص
                                  ),
                                ),
                              ),
                          ),
                        ],
                      ),
                       if (resource.description.isNotEmpty)
                        Padding(
                           padding: const EdgeInsets.only(top: 4.0, right: 18), // زيادة المسافة اليمنى للمحاذاة
                          child: Text(
                            resource.description,
                            style: textTheme.bodySmall?.copyWith(color: Colors.grey.shade700, height: 1.4),
                          ),
                        ),
                    ],
                  ),
                ),
                const SizedBox(width: 10),
                // --- النوع ---
                Padding(
                  padding: const EdgeInsets.only(top: 4.0), // ضبط محاذاة الشارة رأسياً
                  child: _buildTypeBadge(context, resource.type),
                ),
              ],
            ),
            const SizedBox(height: 12),

            // --- فاصل ---
            Divider(height: 1, color: Colors.grey.shade300),
            const SizedBox(height: 12),

            // --- الصف الثاني: التفاصيل (الموضوع، العمر، الرابط) ---
             Wrap( // استخدام Wrap لتوزيع العناصر بشكل جيد
              spacing: 12.0, // المسافة الأفقية بين العناصر
              runSpacing: 6.0, // المسافة العمودية إذا انتقل لسطر جديد
              children: [
                 if(resource.subject.isNotEmpty && resource.subject != '-') // إخفاء الموضوع إذا كان فارغاً أو "-"
                    _buildInfoChip(context, Icons.topic_outlined, 'الموضوع', resource.subject),
                 if(resource.targetAge.isNotEmpty)
                    _buildInfoChip(context, Icons.child_care_outlined, 'العمر', resource.targetAge),
                 _buildInfoChip(context, Icons.link, 'الرابط', resource.url, isLink: true),
              ],
            ),

            const SizedBox(height: 12),

            // --- الصف الثالث: معلومات الإضافة والإجراءات (إزالة الأزرار غير المفعّلة) ---
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              crossAxisAlignment: CrossAxisAlignment.center,
              children: [
                Flexible(
                  child: Text(
                    'أضيف بواسطة: ${resource.addedBy} في ${resource.dateAdded}',
                    style: textTheme.bodySmall?.copyWith(color: Colors.grey.shade600),
                    overflow: TextOverflow.ellipsis,
                    maxLines: 1,
                  ),
                ),
                const SizedBox(width: 10),
                // لا يوجد أي أزرار أو إجراءات في هذا الإصدار للعرض فقط
              ],
            ),
          ],
        ),
      ),
    );
  }
}
```

#### `lib/screens/child_features/upcoming_events_mobile_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';
import 'package:intl/date_symbol_data_local.dart'; // لاستيراد بيانات تنسيق التاريخ للغة

// =======================================================
// نموذج بيانات الفعالية القادمة
// =======================================================
class UpcomingEvent {
  final int id;
  final String name;
  final DateTime dateTime;
  final String location;
  final bool requiresRegistration;
  final DateTime? registrationDeadline;
  final int registeredCount;
  final String createdBy;

  UpcomingEvent({
    required this.id,
    required this.name,
    required this.dateTime,
    required this.location,
    required this.requiresRegistration,
    this.registrationDeadline,
    required this.registeredCount,
    required this.createdBy,
  });
}

// =======================================================
// الكلاس الرئيسي للشاشة
// =======================================================
class UpcomingEventsMobileScreen extends StatefulWidget {
  const UpcomingEventsMobileScreen({Key? key}) : super(key: key);

  @override
  State<UpcomingEventsMobileScreen> createState() => _UpcomingEventsMobileScreenState();
}

class _UpcomingEventsMobileScreenState extends State<UpcomingEventsMobileScreen> {

  // --- بيانات تجريبية ---
  final List<UpcomingEvent> upcomingEvents = [
    UpcomingEvent(id: 1, name: 'رحلة إلى قلعة حماه الأثرية', dateTime: DateTime(2025, 6, 1, 9, 0), location: 'قلعة حماه', requiresRegistration: false, registrationDeadline: null, registeredCount: 0, createdBy: 'مدير النظام'),
    UpcomingEvent(id: 2, name: 'المعسكر الصيفي للعلوم وتكنولوجيا الروبوتات المتقدمة', dateTime: DateTime(2025, 7, 10, 10, 30), location: 'مختبر المدرسة المركزي والورش الملحقة والمكتبة الرقمية', requiresRegistration: true, registrationDeadline: DateTime(2025, 6, 25), registeredCount: 15, createdBy: 'قسم العلوم والتكنولوجيا'),
    UpcomingEvent(id: 3, name: 'يوم الأنشطة الرياضية السنوي', dateTime: DateTime(2025, 5, 28, 8, 0), location: 'الملعب الرئيسي والصالات المغطاة', requiresRegistration: false, registrationDeadline: null, registeredCount: 0, createdBy: 'قسم الرياضة'),
     UpcomingEvent(id: 4, name: 'ورشة عمل فن الخط العربي', dateTime: DateTime(2025, 8, 15, 14, 0), location: 'قاعة الفنون بالمدرسة', requiresRegistration: true, registrationDeadline: DateTime(2025, 8, 1), registeredCount: 8, createdBy: 'نادي الفنون'),
  ];

  @override
  void initState() {
    super.initState();
    _initializeArabicFormatting();
  }

  // دالة منفصلة لتهيئة اللغة
  Future<void> _initializeArabicFormatting() async {
    try {
       await initializeDateFormatting('ar');
    } catch (e) {
      print("Error initializing date formatting for 'ar': $e");
    }
  }


  // --- دوال مساعدة للتنسيق (باستخدام تنسيقات عربية محسنة) ---
  String _formatDate(DateTime? date) {
    if (date == null) return '-';
    try {
      return DateFormat('EEEE، d MMMM y', 'ar').format(date);
    } catch (e) {
      return DateFormat('yyyy-MM-dd').format(date);
    }
  }
  String _formatShortDate(DateTime? date) {
    if (date == null) return '-';
    try {
      return DateFormat('yyyy/MM/dd', 'ar').format(date);
    } catch (e) {
      return DateFormat('yyyy/MM/dd').format(date);
    }
  }
  String _formatTime(DateTime? date) {
    if (date == null) return '--:--';
     try {
       return DateFormat('hh:mm a', 'ar').format(date);
     } catch (e) {
        return DateFormat('HH:mm').format(date);
     }
  }
  String _formatFullDateTime(DateTime? date) {
    if (date == null) return '-';
    try {
      return '${_formatDate(date)} الساعة ${_formatTime(date)}';
    } catch (e) {
      return DateFormat('yyyy-MM-dd HH:mm').format(date);
    }
  }
  // ----------------------------------------------------------

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: _buildAppBar(context),
      body: _buildBody(),
      backgroundColor: Theme.of(context).scaffoldBackgroundColor, // استخدام لون الخلفية من الثيم
    );
  }

  // =======================================================
  // AppBar بتصميم أكثر احترافية
  // =======================================================
  AppBar _buildAppBar(BuildContext context) {
    return AppBar(
      // استخدام لون أساسي من الثيم (أو تحديد لون احترافي ثابت)
      backgroundColor: Theme.of(context).appBarTheme.backgroundColor,
      foregroundColor: Theme.of(context).appBarTheme.foregroundColor,
      elevation: 1.0,
      title: Text(
        'الفعاليات القادمة',
        style: Theme.of(context).appBarTheme.titleTextStyle,
      ),
      centerTitle: true,
      leading: Navigator.canPop(context)
          ? IconButton(
              icon: const Icon(Icons.arrow_back),
              tooltip: 'رجوع',
              splashRadius: 24,
              onPressed: () => Navigator.pop(context),
            )
          : null,
    );
  }

  // =======================================================
  // محتوى الشاشة الرئيسي
  // =======================================================
  Widget _buildBody() {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Padding(
          padding: const EdgeInsetsDirectional.fromSTEB(20.0, 24.0, 20.0, 16.0),
          child: Text(
            'القائمة الحالية للفعاليات المرتقبة',
            textAlign: TextAlign.start,
            style: Theme.of(context).textTheme.titleLarge?.copyWith(
                  fontWeight: FontWeight.w600,
                  color: Colors.teal[900],
                ),
          ),
        ),
        Expanded(
          child: upcomingEvents.isEmpty
              ? _buildEmptyState()
              : _buildEventsList(),
        ),
      ],
    );
  }

  // =======================================================
  // بناء قائمة الفعاليات باستخدام ListView.builder
  // =======================================================
  Widget _buildEventsList() {
    return ListView.builder(
      padding: const EdgeInsets.symmetric(horizontal: 16.0, vertical: 8.0),
      itemCount: upcomingEvents.length,
      itemBuilder: (context, index) {
        final event = upcomingEvents[index];
        return Padding(
          padding: const EdgeInsets.only(bottom: 16.0),
          child: _buildEventCard(context, event),
        );
      },
    );
  }


  // =======================================================
  // ويدجت لعرض حالة عدم وجود فعاليات بتصميم محسن
  // =======================================================
  Widget _buildEmptyState() {
    return Center(
      child: Padding(
        padding: const EdgeInsets.all(32.0),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(Icons.event_note_sharp, size: 90, color: Colors.grey[400]),
            const SizedBox(height: 24),
            Text(
              'لا توجد فعاليات قادمة بعد.',
              textAlign: TextAlign.center,
              style: Theme.of(context).textTheme.headlineSmall?.copyWith(
                    color: Colors.grey[600],
                    fontWeight: FontWeight.w500,
                  ),
            ),
            const SizedBox(height: 12),
            Text(
              'سيتم عرض الفعاليات الجديدة هنا فور إضافتها من قبل الإدارة.',
              textAlign: TextAlign.center,
              style: Theme.of(context).textTheme.bodyMedium?.copyWith(
                    color: Colors.grey[500],
                    height: 1.4,
                  ),
            ),
          ],
        ),
      ),
    );
  }

  // =======================================================
  // بناء بطاقة الفعالية بتصميم أكثر احترافية وجاذبية
  // =======================================================
  Widget _buildEventCard(BuildContext context, UpcomingEvent event) {
    final Color primaryTextColor = Colors.grey[850]!;
    final Color secondaryTextColor = Colors.grey[600]!;
    final Color highlightColor = Theme.of(context).colorScheme.primary;
    final Color cardBackgroundColor = Theme.of(context).cardTheme.color!;
    final Color subtleBorderColor = Colors.grey[200]!;

    return Card(
      margin: EdgeInsets.zero,
      elevation: 2.5,
      shadowColor: Colors.black.withOpacity(0.15),
      color: cardBackgroundColor,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(14.0),
        side: BorderSide(color: subtleBorderColor, width: 0.8),
      ),
      clipBehavior: Clip.antiAlias,
      child: InkWell(
        onTap: () {
           _showEventDetailsModal(context, event);
        },
        splashColor: highlightColor.withOpacity(0.1),
        highlightColor: highlightColor.withOpacity(0.05),
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Text(
                event.name,
                style: Theme.of(context).textTheme.titleMedium?.copyWith(
                      fontWeight: FontWeight.bold,
                      color: primaryTextColor,
                      height: 1.4,
                    ),
                maxLines: 2,
                overflow: TextOverflow.ellipsis,
              ),
              const SizedBox(height: 12.0),

              _buildInfoRow(
                context,
                icon: Icons.access_time_rounded,
                text: _formatFullDateTime(event.dateTime),
                textColor: secondaryTextColor,
              ),
              const SizedBox(height: 8.0),

               _buildInfoRow(
                context,
                icon: Icons.location_on_outlined,
                text: event.location,
                textColor: highlightColor,
                isLocation: true,
              ),

              Divider(height: 28.0, thickness: 0.7, color: subtleBorderColor),

              _buildDetailRowWidget(
                 context,
                 icon: Icons.how_to_reg_outlined,
                 label: "يتطلب تسجيل؟",
                 childWidget: _buildRegistrationStatusChip(context, event.requiresRegistration),
                 vPadding: 6.0,
              ),

              if (event.requiresRegistration) ...[
                 _buildDetailRow(
                   context,
                   icon: Icons.event_busy_outlined,
                   label: "آخر موعد:",
                   value: _formatShortDate(event.registrationDeadline),
                   vPadding: 6.0,
                 ),
                 _buildDetailRow(
                   context,
                   icon: Icons.group_outlined,
                   label: "المسجلون:",
                   value: '${event.registeredCount} ${event.registeredCount > 0 ? "مشارك" : ""}',
                   valueWeight: FontWeight.w600,
                   vPadding: 6.0,
                 ),
              ],

               _buildDetailRow(
                 context,
                 icon: Icons.person_pin_outlined,
                 label: "الجهة:",
                 value: event.createdBy,
                 vPadding: 6.0,
                 valueColor: secondaryTextColor,
               ),
            ],
          ),
        ),
      ),
    );
  }

   // =======================================================
  // دالة مساعدة لبناء صف بسيط (أيقونة + نص) - مثل التاريخ والموقع
  // =======================================================
   Widget _buildInfoRow(BuildContext context, {required IconData icon, required String text, required Color textColor, bool isLocation = false}) {
    return Row(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Icon(icon, size: 18, color: Colors.grey[500]),
        const SizedBox(width: 8.0),
        Expanded(
          child: Text(
            text,
            textAlign: TextAlign.start,
            style: Theme.of(context).textTheme.bodyMedium?.copyWith(
              color: textColor,
              fontWeight: isLocation ? FontWeight.w500 : FontWeight.normal,
              height: 1.4,
            ),
             maxLines: isLocation ? 2 : 1,
             overflow: TextOverflow.ellipsis,
          ),
        ),
      ],
    );
  }

  // =======================================================
  // دالة مساعدة لبناء صف تفاصيل (أيقونة، تسمية، قيمة نصية)
  // =======================================================
  Widget _buildDetailRow(BuildContext context, {required IconData icon, required String label, required String value, Color? valueColor, FontWeight? valueWeight, double vPadding = 8.0}) {
    final bool isPlaceholder = value == '-';
    final Color defaultColor = Colors.grey[800]!;
    final Color effectiveValueColor = isPlaceholder ? Colors.grey.shade500 : (valueColor ?? defaultColor);
    final FontWeight effectiveValueWeight = isPlaceholder ? FontWeight.normal : (valueWeight ?? FontWeight.w500);
    final Color labelColor = Colors.grey[600]!;

    return Padding(
      padding: EdgeInsets.symmetric(vertical: vPadding),
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Icon(icon, size: 18, color: labelColor),
          const SizedBox(width: 8.0),
          SizedBox(
            width: 100,
            child: Text(
              label,
              style: Theme.of(context).textTheme.bodyMedium?.copyWith(color: labelColor),
              maxLines: 1,
              overflow: TextOverflow.ellipsis,
            ),
          ),
          const SizedBox(width: 6.0),
          Expanded(
            child: Text(
              value,
              textAlign: TextAlign.start,
              style: Theme.of(context).textTheme.bodyMedium?.copyWith(
                color: effectiveValueColor,
                fontWeight: effectiveValueWeight,
                height: 1.3,
              ),
            ),
          ),
        ],
      ),
    );
  }

  // =======================================================
  // دالة مساعدة لبناء صف تفاصيل (أيقونة، تسمية، ويدجت مخصصة كقيمة)
  // =======================================================
   Widget _buildDetailRowWidget(BuildContext context, {required IconData icon, required String label, required Widget childWidget, double vPadding = 8.0}) {
     final Color labelColor = Colors.grey[600]!;
     return Padding(
       padding: EdgeInsets.symmetric(vertical: vPadding),
       child: Row(
        crossAxisAlignment: CrossAxisAlignment.center,
        children: [
          Icon(icon, size: 18, color: labelColor),
          const SizedBox(width: 8.0),
          SizedBox(
             width: 100,
             child: Text(
               label,
               style: Theme.of(context).textTheme.bodyMedium?.copyWith(color: labelColor),
               maxLines: 1,
               overflow: TextOverflow.ellipsis,
             ),
           ),
          const SizedBox(width: 6.0),
          Flexible(child: childWidget),
        ],
      ),
     );
   }

  // =======================================================
  // بناء مؤشر بصري لحالة التسجيل باستخدام Chip
  // =======================================================
  Widget _buildRegistrationStatusChip(BuildContext context, bool requiresRegistration) {
    final Color chipBackgroundColor = requiresRegistration ? Colors.orange.shade50 : Colors.green.shade50;
    final Color chipForegroundColor = requiresRegistration ? Colors.orange.shade800 : Colors.green.shade800;
    final IconData chipIcon = requiresRegistration ? Icons.check_circle_outline : Icons.highlight_off;

    return Chip(
      avatar: Icon(chipIcon, size: 16, color: chipForegroundColor),
      label: Text(
        requiresRegistration ? 'مطلوب' : 'غير مطلوب',
        style: TextStyle(
          color: chipForegroundColor,
          fontSize: 12,
          fontWeight: FontWeight.w600,
        ),
      ),
      backgroundColor: chipBackgroundColor,
      padding: const EdgeInsets.symmetric(horizontal: 8, vertical: 2),
      shape: StadiumBorder(side: BorderSide(color: chipForegroundColor.withOpacity(0.3), width: 0.5)),
      materialTapTargetSize: MaterialTapTargetSize.shrinkWrap,
      visualDensity: VisualDensity.compact,
    );
  }

   // =======================================================
  // دالة لعرض تفاصيل الفعالية في Modal Bottom Sheet
  // =======================================================
  void _showEventDetailsModal(BuildContext context, UpcomingEvent event) {
    showModalBottomSheet(
      context: context,
      isScrollControlled: true,
      shape: const RoundedRectangleBorder(
        borderRadius: BorderRadius.vertical(top: Radius.circular(20.0)),
      ),
      builder: (ctx) {
        return Wrap(
          children: [
            Padding(
              padding: const EdgeInsets.all(24.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                   Text(
                     event.name,
                     textAlign: TextAlign.start,
                     style: Theme.of(context).textTheme.headlineSmall?.copyWith(fontWeight: FontWeight.bold),
                   ),
                  const SizedBox(height: 16),
                   _buildInfoRow(
                     context,
                     icon: Icons.access_time_rounded,
                     text: _formatFullDateTime(event.dateTime),
                     textColor: Colors.grey[700]!,
                   ),
                   const SizedBox(height: 10),
                   _buildInfoRow(
                     context,
                     icon: Icons.location_on_outlined,
                     text: event.location,
                     textColor: Theme.of(context).colorScheme.primary,
                     isLocation: true,
                   ),
                   const Divider(height: 32),
                   _buildDetailRowWidget(
                      context,
                      icon: Icons.how_to_reg_outlined,
                      label: "التسجيل:",
                      childWidget: _buildRegistrationStatusChip(context, event.requiresRegistration),
                      vPadding: 4,
                   ),
                    if (event.requiresRegistration) ...[
                      _buildDetailRow(
                        context,
                        icon: Icons.event_busy_outlined,
                        label: "آخر موعد:",
                        value: _formatShortDate(event.registrationDeadline),
                         vPadding: 4,
                      ),
                      _buildDetailRow(
                        context,
                        icon: Icons.group_outlined,
                        label: "المسجلون:",
                        value: '${event.registeredCount} مشارك',
                        valueWeight: FontWeight.bold,
                         vPadding: 4,
                      ),
                   ],
                   _buildDetailRow(
                     context,
                     icon: Icons.person_pin_outlined,
                     label: "الجهة:",
                     value: event.createdBy,
                      vPadding: 4,
                     valueColor: Colors.grey[700]!,
                   ),
                   const SizedBox(height: 24),
                   Align(
                     alignment: AlignmentDirectional.centerEnd,
                     child: TextButton(
                       onPressed: () => Navigator.pop(ctx),
                       child: const Text('إغلاق'),
                     ),
                   )
                ],
              ),
            ),
          ],
        );
      },
    );
  }
}
```

#### `lib/screens/child_features/teacher_notes_display_page.dart`

```dart
import 'package:flutter/material.dart';

// --- صفحة عرض ملاحظات المعلم (للعرض فقط) ---
class TeacherNotesDisplayPage extends StatelessWidget {
  const TeacherNotesDisplayPage({super.key});

  // --- قائمة الملاحظات (لأغراض العرض فقط في هذا المثال) ---
  // في تطبيق حقيقي، هذه البيانات ستأتي من مصدر آخر (مثل API أو قاعدة بيانات)
  // وسيتم تمريرها إلى هذه الصفحة عبر المُنشئ الخاص بها.
  final List<String> notes = const [
    'تذكير: غدًا نشاط رسم حر 🖌️',
    'يرجى إرسال الزي الرياضي يوم الخميس 👟',
    'مراجعة الحروف من أ إلى د 🅰️',
    'لا تنسوا قراءة قصة نهاية الأسبوع 📚',
    'تجهيز الأدوات لمشروع إعادة التدوير ♻️',
  ];

  // --- دالة مساعدة لبناء بطاقة الملاحظة (لتحسين القراءة) ---
  Widget _buildNoteCard(int index, BuildContext context, List<String> notesData) {
    final theme = Theme.of(context);
    // تحديد أيقونة مناسبة
    IconData leadingIcon = Icons.push_pin_outlined;
    if (notesData[index].contains('تذكير') || notesData[index].contains('غدًا')) {
      leadingIcon = Icons.event_note_outlined;
    } else if (notesData[index].contains('إرسال') || notesData[index].contains('رياضي')) {
      leadingIcon = Icons.directions_run_outlined;
    } else if (notesData[index].contains('حروف') || notesData[index].contains('مراجعة')) {
      leadingIcon = Icons.menu_book_outlined;
    } else if (notesData[index].contains('قصة') || notesData[index].contains('قراءة')) {
      leadingIcon = Icons.auto_stories_outlined;
    } else if (notesData[index].contains('مشروع') || notesData[index].contains('أدوات')) {
      leadingIcon = Icons.construction_outlined;
    }

    return Card(
      color: Colors.white,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(15),
      ),
      elevation: 2,
      margin: const EdgeInsets.symmetric(vertical: 8, horizontal: 4),
      child: ListTile(
        contentPadding: EdgeInsets.symmetric(vertical: 12, horizontal: 16),
        leading: Icon(leadingIcon, color: theme.colorScheme.tertiary, size: 28), // لون من الثيم
        title: Text(
          notesData[index],
          style: theme.textTheme.titleMedium?.copyWith(
            height: 1.4,
          ),
        ),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);

    return Scaffold(
      backgroundColor: theme.scaffoldBackgroundColor,
      appBar: AppBar(
        title: const Text(
          'ملاحظات المعلم',
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 18),
        ),
        centerTitle: true,
        // ألوان AppBar من الثيم
      ),
      body: notes.isEmpty
            // --- حالة القائمة فارغة ---
            ? Center(
                child: Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Icon(Icons.notes_outlined, size: 80, color: Colors.grey.shade400),
                    SizedBox(height: 16),
                    Text(
                      'لا توجد ملاحظات لعرضها',
                      style: theme.textTheme.headlineSmall?.copyWith(color: Colors.grey.shade600),
                    ),
                  ],
                ),
              )
            // --- حالة وجود ملاحظات ---
            : ListView.builder(
                padding: const EdgeInsets.all(12.0),
                itemCount: notes.length,
                itemBuilder: (context, index) {
                  return _buildNoteCard(index, context, notes);
                },
              ),
    );
  }
}
```

#### `lib/screens/child_features/class_overview_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:kids/screens/child_features/student_media_gallery_screen.dart'; // تأكد أن هذا المسار صحيح

// يفضل تسمية الكلاس بحرف كبير في البداية إذا كان يمثل واجهة مستخدم رئيسية
class ClassOverviewScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // لتحديد ارتفاع البطاقات بناءً على ارتفاع الشاشة المتاح
    // يمكن تعديل هذا العامل (0.35) لزيادة أو تقليل ارتفاع البطاقة
    final double cardHeight = MediaQuery.of(context).size.height * 0.38;
    final double cardWidth = MediaQuery.of(context).size.width * 0.9;
    final theme = Theme.of(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('الفصول الدراسية'), // عنوان أكثر وصفًا
        centerTitle: true,
        backgroundColor: theme.appBarTheme.backgroundColor, // لون مختلف للـ AppBar
        elevation: 2,
      ),
      body: SafeArea( // لاستيعاب النوتش والحواف بأمان
        child: SingleChildScrollView( // للسماح بالتمرير إذا أصبحت البطاقات أطول من الشاشة
          padding: const EdgeInsets.symmetric(horizontal: 16.0, vertical: 20.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              _buildInteractiveCard(
                context: context,
                title: 'الفئة A',
                subtitle: 'استكشف أنشطة ومشاريع فئة ألفا الإبداعية.',
                imageUrl: 'assets/31.png', // استبدل بالمسار الصحيح
                destinationPage: StudentMediaGalleryScreen(), // أو صفحة خاصة بالفئة أ
                cardHeight: cardHeight,
                cardWidth: cardWidth,
                primaryColor: theme.colorScheme.primary, // استخدام لون الثيم الأساسي
              ),
              SizedBox(height: 20), // مسافة بين البطاقتين
              _buildInteractiveCard(
                context: context,
                title: 'الفئة B',
                subtitle: 'انغمس في عالم فئة بيتا المليء بالمعرفة والمرح.',
                imageUrl: 'assets/32.png', // استبدل بالمسار الصحيح
                destinationPage: StudentMediaGalleryScreen(), // أو صفحة خاصة بالفئة ب
                cardHeight: cardHeight,
                cardWidth: cardWidth,
                primaryColor: theme.colorScheme.primary,
              ),
              // يمكنك إضافة المزيد من البطاقات هنا
            ],
          ),
        ),
      ),
    );
  }

  Widget _buildInteractiveCard({
    required BuildContext context,
    required String title,
    required String subtitle,
    required String imageUrl,
    required Widget destinationPage,
    required double cardHeight,
    required double cardWidth,
    required Color primaryColor,
  }) {
    return SizedBox(
      height: cardHeight,
      width: cardWidth,
      child: Card(
        elevation: 8.0,
        clipBehavior: Clip.antiAlias, // مهم لقص الصورة بشكل صحيح مع حواف البطاقة
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(20.0),
        ),
        child: InkWell(
          onTap: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => destinationPage),
            );
          },
          child: Stack(
            fit: StackFit.expand, // لجعل الصورة تملأ البطاقة
            children: <Widget>[
              // 1. الصورة الخلفية
              Image.asset(
                imageUrl,
                fit: BoxFit.cover,
                errorBuilder: (context, error, stackTrace) {
                  return Container(
                    color: Colors.grey[300],
                    child: Center(child: Icon(Icons.broken_image, size: 50, color: Colors.grey[600])),
                  );
                },
              ),
              // 2. تراكب متدرج لضمان وضوح النص
              Container(
                decoration: BoxDecoration(
                  gradient: LinearGradient(
                    colors: [
                      Colors.black.withOpacity(0.0), // شفاف في الأعلى
                      Colors.black.withOpacity(0.2),
                      Colors.black.withOpacity(0.8)  // أغمق في الأسفل حيث النص
                    ],
                    begin: Alignment.topCenter,
                    end: Alignment.bottomCenter,
                    stops: [0.0, 0.5, 1.0], // تحكم في توزيع التدرج
                  ),
                ),
              ),
              // 3. المحتوى النصي
              Positioned(
                bottom: 20.0,
                left: 20.0,
                right: 20.0,
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  mainAxisSize: MainAxisSize.min,
                  children: <Widget>[
                    Text(
                      title,
                      style: TextStyle(
                        fontSize: 24, // حجم أكبر للعنوان
                        fontWeight: FontWeight.bold,
                        color: Colors.white,
                        shadows: [ // ظل خفيف للنص لزيادة الوضوح
                          Shadow(
                            blurRadius: 2.0,
                            color: Colors.black.withOpacity(0.5),
                            offset: Offset(1.0, 1.0),
                          ),
                        ],
                      ),
                    ),
                    SizedBox(height: 8),
                    Text(
                      subtitle,
                      style: TextStyle(
                        fontSize: 15,
                        color: Colors.white.withOpacity(0.9), // لون أفتح قليلاً للوصف
                      ),
                      maxLines: 2,
                      overflow: TextOverflow.ellipsis,
                    ),
                  ],
                ),
              ),
              // 4. (اختياري) أيقونة أو مؤشر في الزاوية
              Positioned(
                top: 15.0,
                right: 15.0,
                child: Container(
                  padding: EdgeInsets.all(8),
                  decoration: BoxDecoration(
                    color: primaryColor.withOpacity(0.8),
                    shape: BoxShape.circle,
                  ),
                  child: Icon(Icons.arrow_forward_ios, color: Colors.white, size: 18),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

#### `lib/screens/educational_games/games_gallery.dart`

```dart
import 'package:flutter/material.dart';
import 'package:kids/screens/educational_games/bubble_pop_game.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/drag_and_drop_game.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/coloring_game.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/counting_game.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/memory_game_page.dart'; // تم تحديث المسار
import 'package:kids/screens/educational_games/maze_game.dart'; // تم تحديث المسار


class GamesGallery extends StatelessWidget {
  final List<Game> games = [
    Game(title: "لعبة التلوين", icon: Icons.brush, page: ColoringGame()),
    Game(title: "لعبة الذاكرة", icon: Icons.memory, page: MemoryGamePage()),
    Game(title: "لعبة الأشكال", icon: Icons.crop_square, page: CountingGame()),
    Game(title: "لعبة الأحرف", icon: Icons.text_fields, page: DragAndDropGame()),
    Game(title: "لعبة الهروب من المتاهة", icon: Icons.assistant_photo_outlined, page: MazeGame()),
    Game(title: "لعبة الفقاعات", icon: Icons.circle_outlined, page: BubblePopGame()),
  ];

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: Text("معرض الألعاب للأطفال"),
        backgroundColor: theme.appBarTheme.backgroundColor, // استخدام لون الثيم
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [theme.colorScheme.secondary.withOpacity(0.2), theme.colorScheme.primary.withOpacity(0.2)], // تدرج لوني من الثيم
            begin: Alignment.topLeft,
            end: Alignment.bottomRight,
          ),
        ),
        child: GridView.builder(
          padding: EdgeInsets.all(16),
          gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
            crossAxisCount: 2,
            crossAxisSpacing: 16,
            mainAxisSpacing: 16,
            childAspectRatio: 0.8,
          ),
          itemCount: games.length,
          itemBuilder: (context, index) {
            return GestureDetector(
              onTap: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => games[index].page),
                );
              },
              child: AnimatedContainer(
                duration: Duration(milliseconds: 300),
                decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(20),
                  color: Colors.white.withOpacity(0.85), // لون أبيض مع شفافية
                  boxShadow: [
                    BoxShadow(
                      color: Colors.black26.withOpacity(0.1), // ظل أخف
                      blurRadius: 10,
                      spreadRadius: 2,
                    ),
                  ],
                ),
                child: Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Icon(
                      games[index].icon,
                      size: 60,
                      color: theme.colorScheme.primary, // استخدام لون الثيم الأساسي
                    ),
                    SizedBox(height: 10),
                    Text(
                      games[index].title,
                      style: theme.textTheme.titleMedium?.copyWith(
                        color: theme.colorScheme.primary,
                        fontWeight: FontWeight.bold,
                      ),
                      textAlign: TextAlign.center,
                    ),
                  ],
                ),
              ),
            );
          },
        ),
      ),
    );
  }
}

class Game {
  final String title;
  final IconData icon;
  final Widget page;

  Game({required this.title, required this.icon, required this.page});
}
```

#### `lib/screens/educational_games/bubble_pop_game.dart`

```dart
import 'package:flutter/material.dart';
import 'dart:async';
import 'dart:math';
import 'package:audioplayers/audioplayers.dart';

// يجب أن يتم تهيئة AudioPlayer مرة واحدة فقط
final AudioPlayer _player = AudioPlayer();

class BubblePopGame extends StatefulWidget {
  @override
  _BubblePopGameState createState() => _BubblePopGameState();
}

class _BubblePopGameState extends State<BubblePopGame> {
  int score = 0;
  int targetBubbles = 10;
  Timer? gameTimer;
  bool isGameOver = false;
  List<Offset> bubblePositions = [];
  List<Color> bubbleColors = [Colors.red, Colors.green, Colors.yellow, Colors.purple, Colors.orange];
  final Random _random = Random(); // لضمان عشوائية أفضل

  @override
  void initState() {
    super.initState();
    startGame();
  }

  void startGame() {
    setState(() {
      score = 0;
      isGameOver = false;
      bubblePositions.clear();
    });

    gameTimer?.cancel(); // إلغاء أي مؤقت سابق
    gameTimer = Timer.periodic(Duration(milliseconds: 700), (timer) { // توليد فقاعات أسرع قليلاً
      if (isGameOver) {
        gameTimer?.cancel();
      } else {
        spawnBubble();
      }
    });
  }

  void spawnBubble() {
    if (!isGameOver) {
      // الحصول على أبعاد الشاشة لتوليد فقاعات داخلها
      final screenWidth = MediaQuery.of(context).size.width;
      final screenHeight = MediaQuery.of(context).size.height;

      setState(() {
        // توليد موقع عشوائي آمن (بعيدًا عن الحواف)
        final randomX = _random.nextDouble() * (screenWidth - 120) + 60; // 60 لكل جانب للفقاعة
        final randomY = _random.nextDouble() * (screenHeight - 120 - AppBar().preferredSize.height - (Scaffold.of(context).hasFloatingActionButton ? 80 : 0)) + 60; // استبعاد الـ AppBar ومساحة زر FAB
        bubblePositions.add(Offset(randomX, randomY));
      });
    }
  }

  void playPopSound() {
    _player.play(AssetSource('pop_sound.mp3')); // تأكد من إضافة الملف إلى assets
  }

  void popBubble(Offset position) { // تم إزالة color غير المستخدم
    setState(() {
      score++;
      bubblePositions.remove(position);
      playPopSound();
      if (score >= targetBubbles) {
        isGameOver = true;
        gameTimer?.cancel();
      }
    });
  }

  void _showGameOverDialog() {
    showDialog(
      context: context,
      barrierDismissible: false, // لا يمكن إغلاقها بالنقر خارجها
      builder: (context) {
        return AlertDialog(
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20)),
          title: Text(
            "انتهت اللعبة!",
            textAlign: TextAlign.center,
            style: TextStyle(fontWeight: FontWeight.bold, color: Theme.of(context).primaryColor),
          ),
          content: Text(
            "لقد فجرت $score فقاعات! هل تريد اللعب مرة أخرى؟",
            textAlign: TextAlign.center,
            style: TextStyle(fontSize: 16),
          ),
          actionsAlignment: MainAxisAlignment.center,
          actions: [
            ElevatedButton(
              onPressed: () {
                Navigator.of(context).pop();
                startGame();
              },
              style: ElevatedButton.styleFrom(
                backgroundColor: Theme.of(context).colorScheme.secondary,
                shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
                padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10)
              ),
              child: Text("نعم، مرة أخرى"),
            ),
            TextButton(
              onPressed: () {
                Navigator.of(context).pop();
                Navigator.of(context).pop(); // العودة إلى شاشة الألعاب
              },
              child: Text("لا، أعود للقائمة"),
              style: TextButton.styleFrom(
                foregroundColor: Colors.grey.shade600
              ),
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    if (isGameOver) {
      WidgetsBinding.instance.addPostFrameCallback((_) => _showGameOverDialog());
    }

    return Scaffold(
      appBar: AppBar(
        title: Text("لعبة تفجير الفقاعات"),
        backgroundColor: Theme.of(context).appBarTheme.backgroundColor,
      ),
      body: GestureDetector(
        onTapUp: (details) {
          // للتعامل مع النقر على الخلفية بدون فقاعة
          // إذا كان الهدف هو تفجير الفقاعات فقط، فقم بإزالة هذا الجزء
          // (لا يحتاج الكود الأصلي لهذا لأنه يعالج onTap على الفقاعات مباشرة)
          if (!isGameOver) {
            print("Tapped on background");
          }
        },
        child: Stack(
          children: [
            Container(
              decoration: BoxDecoration(
                gradient: LinearGradient(
                  colors: [Theme.of(context).colorScheme.primary.withOpacity(0.3), Theme.of(context).colorScheme.background],
                  begin: Alignment.topLeft,
                  end: Alignment.bottomRight,
                ),
              ),
            ),
            // عرض الفقاعات
            ...bubblePositions.map((position) {
              Color bubbleColor = bubbleColors[_random.nextInt(bubbleColors.length)];
              return Positioned(
                left: position.dx,
                top: position.dy,
                child: GestureDetector(
                  onTap: () {
                    popBubble(position); // تم تبسيط الاستدعاء
                  },
                  child: AnimatedContainer(
                    duration: Duration(milliseconds: 200),
                    width: 60,
                    height: 60,
                    decoration: BoxDecoration(
                      color: bubbleColor,
                      shape: BoxShape.circle,
                      boxShadow: [
                        BoxShadow(
                          blurRadius: 10,
                          spreadRadius: 2,
                          color: Colors.black.withOpacity(0.3),
                        ),
                      ],
                    ),
                  ),
                ),
              );
            }),
            // عرض النتيجة
            Positioned(
              top: 20,
              right: 20,
              child: Text(
                "النقاط: $score / $targetBubbles",
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold, color: Theme.of(context).colorScheme.primary),
              ),
            ),
          ],
        ),
      ),
    );
  }

  @override
  void dispose() {
    gameTimer?.cancel();
    _player.dispose(); // التخلص من الـ AudioPlayer
    super.dispose();
  }
}
```

#### `lib/screens/educational_games/counting_game.dart`

```dart
import 'package:flutter/material.dart';

class CountingGame extends StatefulWidget {
  @override
  _CountingGameState createState() => _CountingGameState();
}

class _CountingGameState extends State<CountingGame> {
  int count = 3;
  int? userAnswer; // يمكن أن يكون null قبل الإدخال الأول
  bool? isCorrect; // يمكن أن يكون null (لم يتم التحقق بعد)

  final List<int> itemCounts = [3, 5, 7, 8, 10, 4, 6, 9]; // قائمة أعداد أكبر
  int _currentItemIndex = 0; // مؤشر للرقم الحالي في itemCounts

  final TextEditingController _textController = TextEditingController(); // للتحكم في حقل النص

  @override
  void initState() {
    super.initState();
    _resetGame(); // تهيئة اللعبة في البداية
  }

  void _resetGame() {
    setState(() {
      _currentItemIndex = 0; // ابدأ من أول عدد دائمًا
      itemCounts.shuffle(); // خلط الأعداد لتغيير ترتيب الأسئلة
      count = itemCounts[_currentItemIndex];
      userAnswer = null;
      isCorrect = null;
      _textController.clear(); // مسح حقل النص
    });
  }

  void _nextQuestion() {
    setState(() {
      isCorrect = null; // إعادة تعيين حالة التحقق
      _currentItemIndex = (_currentItemIndex + 1) % itemCounts.length; // التقدم للسؤال التالي
      count = itemCounts[_currentItemIndex];
      userAnswer = null;
      _textController.clear(); // مسح حقل النص
    });
  }

  void _checkAnswer() {
    if (userAnswer == null) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('الرجاء إدخال رقم!')),
      );
      return;
    }
    setState(() {
      isCorrect = (userAnswer == count);
      // لا يتم مسح حقل النص هنا للسماح بالمراجعة إذا كانت الإجابة خاطئة
    });

    if (isCorrect!) {
      Future.delayed(Duration(seconds: 1), () {
        _nextQuestion();
      });
    } else {
       ScaffoldMessenger.of(context).showSnackBar(
         SnackBar(content: Text('إجابة خاطئة! حاول مرة أخرى.', style: TextStyle(color: Colors.white)), backgroundColor: Colors.red.shade600),
       );
    }
  }

  @override
  void dispose() {
    _textController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: Text('لعبة العد'),
        backgroundColor: theme.appBarTheme.backgroundColor,
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [theme.colorScheme.tertiary.withOpacity(0.3), theme.colorScheme.background],
            begin: Alignment.topLeft,
            end: Alignment.bottomRight,
          ),
        ),
        padding: const EdgeInsets.all(16.0),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            Text(
              'كم عدد العناصر التي تراها؟',
              style: theme.textTheme.headlineSmall?.copyWith(color: theme.colorScheme.onBackground),
              textAlign: TextAlign.center,
            ),
            SizedBox(height: 20),
            Expanded(
              child: GridView.builder(
                shrinkWrap: true,
                physics: NeverScrollableScrollPhysics(), // منع التمرير داخل GridView
                gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: count > 6 ? 4 : 3, // ضبط عدد الأعمدة ديناميكياً
                  crossAxisSpacing: 10.0,
                  mainAxisSpacing: 10.0,
                ),
                itemCount: count,
                itemBuilder: (context, index) {
                  return Icon(
                    Icons.apple,
                    size: count > 6 ? 30.0 : 40.0, // ضبط حجم الأيقونة ديناميكياً
                    color: Colors.red.shade600,
                  );
                },
              ),
            ),
            SizedBox(height: 30),
            TextField(
              controller: _textController,
              keyboardType: TextInputType.number,
              textAlign: TextAlign.center, // توسيط النص
              onChanged: (value) {
                setState(() {
                  userAnswer = int.tryParse(value);
                  isCorrect = null; // إعادة تعيين حالة التحقق عند التغيير
                });
              },
              decoration: InputDecoration(
                labelText: 'ادخل العدد هنا',
                labelStyle: TextStyle(color: theme.colorScheme.primary),
                hintStyle: TextStyle(color: Colors.grey.shade500),
                border: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(12),
                  borderSide: BorderSide(color: theme.colorScheme.primary),
                ),
                focusedBorder: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(12),
                  borderSide: BorderSide(color: theme.colorScheme.secondary, width: 2),
                ),
                contentPadding: EdgeInsets.symmetric(vertical: 15, horizontal: 20),
                filled: true,
                fillColor: Colors.white.withOpacity(0.8),
              ),
              style: theme.textTheme.titleMedium?.copyWith(color: Colors.black87),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: _checkAnswer,
              child: Text('تحقق من الإجابة'),
            ),
            SizedBox(height: 20),
            if (isCorrect == true)
              Column(
                children: [
                  Icon(Icons.check_circle_outline, color: Colors.green.shade600, size: 50),
                  Text(
                    'إجابة صحيحة!',
                    style: theme.textTheme.titleLarge?.copyWith(color: Colors.green.shade700),
                  ),
                  SizedBox(height: 10),
                  ElevatedButton(
                    onPressed: _nextQuestion,
                    child: Text('السؤال التالي'),
                  ),
                ],
              ),
            if (isCorrect == false)
              Text(
                'إجابة خاطئة! حاول مرة أخرى.',
                style: theme.textTheme.bodyLarge?.copyWith(color: Colors.red.shade700),
              ),
          ],
        ),
      ),
    );
  }
}
```

#### `lib/screens/educational_games/coloring_game.dart`

```dart
import 'dart:ui' as ui;
import 'package:flutter/material.dart';
import 'package:flutter/rendering.dart';
import 'package:flutter/services.dart';
import 'package:audioplayers/audioplayers.dart';
import 'package:path_provider/path_provider.dart';
import 'dart:io';

class ColoringGame extends StatefulWidget {
  @override
  _ColoringGameState createState() => _ColoringGameState();
}

class _ColoringGameState extends State<ColoringGame> {
  Color selectedColor = Colors.red;
  final AudioPlayer _player = AudioPlayer();
  final GlobalKey _repaintKey = GlobalKey(); // GlobalKey لاستخدامها مع RepaintBoundary

  @override
  void dispose() {
    _player.dispose(); // Dispose the audio player
    super.dispose();
  }

  void playSound(String colorName) async {
    // تأكد من أن assets/sound_files/color_name.mp3 موجودة
    await _player.play(AssetSource('$colorName.mp3')); // ملف الصوت بدون مسار مجلد assets
  }

  void showColorEffect(Color color) {
    final overlay = Overlay.of(context);
    OverlayEntry entry = OverlayEntry(
      builder: (context) => Positioned(
        top: MediaQuery.of(context).size.height * 0.2, // مكان ظاهر
        left: MediaQuery.of(context).size.width / 2 - 40, // توسيط
        child: Material(
          color: Colors.transparent,
          child: Opacity(
            opacity: 0.0,
            child: TweenAnimationBuilder<double>(
              tween: Tween<double>(begin: 0.0, end: 1.0),
              duration: Duration(milliseconds: 600),
              builder: (context, opacity, child) {
                return Opacity(
                  opacity: opacity,
                  child: Transform.scale(
                    scale: opacity,
                    child: Container(
                      padding: EdgeInsets.all(10),
                      decoration: BoxDecoration(
                        color: color.withOpacity(0.7),
                        shape: BoxShape.circle,
                      ),
                      child: Icon(Icons.brush, size: 40, color: Colors.white),
                    ),
                  ),
                );
              },
            ),
          ),
        ),
      ),
    );
    overlay.insert(entry);
    // إزالة OverlayEntry بعد الانتهاء
    Future.delayed(Duration(milliseconds: 800), () => entry.remove());
  }

  Future<void> saveToImage() async {
    RenderRepaintBoundary? boundary = _repaintKey.currentContext?.findRenderObject() as RenderRepaintBoundary?;
    if (boundary == null) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('خطأ: لا يمكن العثور على حدود الرسم للحفظ.')),
      );
      return;
    }
    ui.Image image = await boundary.toImage(pixelRatio: 3.0); // استخدام pixelRatio أعلى لجودة أفضل
    ByteData? byteData = await image.toByteData(format: ui.ImageByteFormat.png);
    if (byteData == null) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('خطأ في تحويل الصورة إلى بايتات.')),
      );
      return;
    }
    final pngBytes = byteData.buffer.asUint8List();

    try {
      final directory = await getApplicationDocumentsDirectory();
      final file = File('${directory.path}/colored_image_${DateTime.now().millisecondsSinceEpoch}.png');
      await file.writeAsBytes(pngBytes);

      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('تم حفظ الصورة بنجاح في: ${file.path}')),
      );
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('خطأ في حفظ الصورة: $e')),
      );
    }
  }

  Map<String, Color> colorMap = {
    'أحمر': Colors.red,
    'أزرق': Colors.blue,
    'أصفر': Colors.yellow,
    'أخضر': Colors.green,
    'برتقالي': Colors.orange,
  };

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('ألواني الجميلة 🎨'),
        backgroundColor: Theme.of(context).appBarTheme.backgroundColor,
        actions: [
          IconButton(
            icon: Icon(Icons.save, color: Theme.of(context).appBarTheme.foregroundColor),
            tooltip: 'حفظ الرسم',
            onPressed: saveToImage,
          ),
        ],
      ),
      body: Column(
        children: [
          SizedBox(height: 20),
          Padding(
            padding: const EdgeInsets.symmetric(horizontal: 16.0),
            child: Wrap(
              spacing: 12, // مسافة أفقية
              runSpacing: 12, // مسافة عمودية بين الصفوف
              alignment: WrapAlignment.center, // توسيط الألوان
              children: colorMap.entries.map((entry) {
                return GestureDetector(
                  onTap: () {
                    setState(() {
                      selectedColor = entry.value;
                    });
                    playSound(entry.key); // تمرير اسم اللون لملف الصوت
                    showColorEffect(entry.value);
                  },
                  child: Container(
                    width: 50,
                    height: 50,
                    decoration: BoxDecoration(
                      color: entry.value,
                      shape: BoxShape.circle,
                      border: Border.all(
                        color: selectedColor == entry.value ? Theme.of(context).colorScheme.primary : Colors.transparent,
                        width: 3,
                      ),
                      boxShadow: [
                        if (selectedColor == entry.value)
                          BoxShadow(
                            color: Theme.of(context).colorScheme.primary.withOpacity(0.5),
                            blurRadius: 8,
                            spreadRadius: 2,
                          ),
                      ],
                    ),
                  ),
                );
              }).toList(),
            ),
          ),
          SizedBox(height: 40),
          Expanded(
            child: RepaintBoundary(
              key: _repaintKey, // تعيين GlobalKey هنا
              child: Container(
                color: Colors.white, // خلفية الرسم بيضاء
                child: Center(
                  child: Wrap(
                    spacing: 20,
                    runSpacing: 20,
                    children: [
                      TappableShape(shape: BoxShape.circle, selectedColor: selectedColor),
                      TappableShape(shape: BoxShape.rectangle, selectedColor: selectedColor),
                      TappableTriangle(selectedColor: selectedColor),
                    ],
                  ),
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

class TappableShape extends StatefulWidget {
  final BoxShape shape;
  final Color selectedColor;

  const TappableShape({required this.shape, required this.selectedColor});

  @override
  _TappableShapeState createState() => _TappableShapeState();
}

class _TappableShapeState extends State<TappableShape> {
  Color? currentColor;

  @override
  void didUpdateWidget(covariant TappableShape oldWidget) {
    super.didUpdateWidget(oldWidget);
    // إذا كانت selectedColor هي نفس currentColor، لا تفعل شيئًا
    // وإلا، يمكنك إزاحة currentColor لإظهار الشكل بلونه الأصلي (الرمادي) إذا أردت
    // أو تركه كما هو لإبقاء اللون المطبق حتى لو غير المستخدم اللون المحدد.
    // الخيار الحالي هو أن الشكل يحافظ على لونه بمجرد النقر عليه.
  }

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () {
        setState(() {
          currentColor = widget.selectedColor;
        });
      },
      child: AnimatedContainer(
        duration: Duration(milliseconds: 300),
        width: 100,
        height: 100,
        decoration: BoxDecoration(
          color: currentColor ?? Colors.grey[300], // لون رمادي كافتراضي
          shape: widget.shape,
          borderRadius: widget.shape == BoxShape.rectangle ? BorderRadius.circular(10) : null,
        ),
      ),
    );
  }
}

class TappableTriangle extends StatefulWidget {
  final Color selectedColor;
  const TappableTriangle({required this.selectedColor});

  @override
  _TappableTriangleState createState() => _TappableTriangleState();
}

class _TappableTriangleState extends State<TappableTriangle> {
  Color? currentColor;

  @override
  void didUpdateWidget(covariant TappableTriangle oldWidget) {
    super.didUpdateWidget(oldWidget);
    // نفس منطق TappableShape
  }

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () {
        setState(() {
          currentColor = widget.selectedColor;
        });
      },
      child: CustomPaint(
        size: Size(100, 100),
        painter: TrianglePainter(color: currentColor ?? Colors.grey[300]),
      ),
    );
  }
}

class TrianglePainter extends CustomPainter {
  final Color color;
  TrianglePainter({required this.color});

  @override
  void paint(Canvas canvas, Size size) {
    final paint = Paint()
      ..color = color
      ..style = PaintingStyle.fill;

    final path = Path()
      ..moveTo(size.width / 2, 0) // نقطة علوية وسطية
      ..lineTo(0, size.height) // نقطة سفلية يسرى
      ..lineTo(size.width, size.height) // نقطة سفلية يمنى
      ..close(); // إغلاق المسار لتكوين المثلث

    canvas.drawPath(path, paint);
  }

  @override
  bool shouldRepaint(covariant TrianglePainter oldDelegate) {
    return oldDelegate.color != color; // إعادة الرسم فقط إذا تغير اللون
  }
}
```

#### `lib/screens/educational_games/drag_and_drop_game.dart`

```dart
import 'package:flutter/material.dart';

class DragAndDropGame extends StatefulWidget {
  @override
  _DragAndDropGameState createState() => _DragAndDropGameState();
}

class _DragAndDropGameState extends State<DragAndDropGame> {
  // قائمة العناصر التي سيتم سحبها (استخدم نسخ قابلة للتعديل)
  List<String> items = [
    '🐶', '🍎', '🐱', '🍌', '🐰', '🍊', '🚗', '🥕', '🍅', '🌶️', '🥔'
  ];

  // قائمة الفئات المتاحة
  final List<String> categories = ['حيوانات', 'فاكهة', 'سيارات', 'خضروات'];

  // لتتبع العناصر الموجودة حاليا في مناطق الإفلات
  Map<String, String?> itemPlacement = {}; // Map: emoji -> categoryName or null

  // لتتبع العناصر التي تم إفلاتها بنجاح ومكانها الصحيح
  final Map<String, String> correctPlacements = {
    '🐶': 'حيوانات', '🍎': 'فاكهة', '🐱': 'حيوانات', '🍌': 'فاكهة',
    '🐰': 'حيوانات', '🍊': 'فاكهة', '🚗': 'سيارات', '🥕': 'خضروات',
    '🍅': 'خضروات', '🌶️': 'خضروات', '🥔': 'خضروات',
  };

  @override
  void initState() {
    super.initState();
    _resetGame();
  }

  void _resetGame() {
    setState(() {
      items = [
        '🐶', '🍎', '🐱', '🍌', '🐰', '🍊', '🚗', '🥕', '🍅', '🌶️', '🥔'
      ]; // إعادة العناصر
      items.shuffle(); // خلط العناصر لزيادة التحدي
      itemPlacement = {}; // مسح أي أماكن سابقة
    });
  }

  bool _isGameComplete() {
    return items.isEmpty; // إذا أصبحت قائمة العناصر فارغة، فقد تم وضع كل شيء
  }

  void _checkAndShowResult() {
    if (!_isGameComplete()) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(
            content: Text('الرجاء سحب كل العناصر إلى أماكنها المناسبة أولاً!')),
      );
      return;
    }

    bool allCorrect = true;
    correctPlacements.forEach((item, correctCategory) {
      if (itemPlacement[item] != correctCategory) {
        allCorrect = false;
        // يمكننا هنا إعطاء مؤشر مرئي للعنصر الخاطئ
      }
    });

    showDialog(
      context: context,
      barrierDismissible: false,
      builder: (context) {
        return AlertDialog(
          title: Text(allCorrect ? 'أحسنت!' : 'حاول مرة أخرى!'),
          content: Text(
              allCorrect
                  ? 'لقد قمت بتصنيف جميع العناصر بشكل صحيح!'
                  : 'يبدو أن بعض العناصر في الفئة الخاطئة. الرجاء المحاولة مرة أخرى.',
              textAlign: TextAlign.center,
          ),
          actions: <Widget>[
            TextButton(
              onPressed: () {
                Navigator.of(context).pop();
                _resetGame();
              },
              child: Text(allCorrect ? 'إعادة اللعبة' : 'المحاولة مجدداً'),
            ),
          ],
        );
      },
    );
  }

  // ودجت بناء منطقة الإفلات (Drop Target)
  Widget _buildDropTarget(String category) {
    final theme = Theme.of(context);
    List<String> itemsInThisCategory = itemPlacement.keys
        .where((item) => itemPlacement[item] == category)
        .toList();

    return DragTarget<String>(
      onWillAccept: (data) {
        // التحقق من أن العنصر يناسب هذه الفئة
        return correctPlacements[data] == category;
      },
      onAccept: (data) {
        setState(() {
          itemPlacement[data] = category;
          items.remove(data); // إزالة العنصر من قائمة العناصر القابلة للسحب
        });
      },
      builder: (context, candidateData, rejectedData) {
        return Container(
          padding: EdgeInsets.all(12),
          width: 90,
          height: 90,
          decoration: BoxDecoration(
            color: itemsInThisCategory.isNotEmpty ? theme.colorScheme.secondary.withOpacity(0.7) : Colors.blueAccent.withOpacity(0.7),
            borderRadius: BorderRadius.circular(15),
            border: Border.all(
                color: candidateData.isNotEmpty ? Colors.white : Colors.transparent,
                width: 2), // تمييز منطقة الإفلات عند السحب فوقها
            boxShadow: [
              BoxShadow(
                color: Colors.black26.withOpacity(0.2),
                blurRadius: 6,
                offset: Offset(0, 4),
              ),
            ],
          ),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text(
                  category,
                  style: theme.textTheme.labelMedium?.copyWith(
                    color: Colors.white,
                    fontSize: 14,
                  ),
                  textAlign: TextAlign.center,
                ),
                Wrap(
                  spacing: 4,
                  children: itemsInThisCategory.map((item) => Text(item, style: TextStyle(fontSize: 18, color: Colors.white))).toList(),
                )
              ],
            ),
          ),
        );
      },
    );
  }

  // ودجت بناء عنصر قابل للسحب (Draggable)
  Widget _buildDraggableItem(String item) {
    return Draggable<String>(
      data: item,
      feedback: Material(
        color: Colors.transparent,
        child: Container(
          padding: EdgeInsets.all(16),
          decoration: BoxDecoration(
            color: Colors.orange.withOpacity(0.8), // لون مميز عند السحب
            borderRadius: BorderRadius.circular(10),
            boxShadow: [
              BoxShadow(
                color: Colors.black38,
                blurRadius: 8,
              ),
            ],
          ),
          child: Text(
            item,
            style: TextStyle(fontSize: 30),
          ),
        ),
      ),
      childWhenDragging: Container(
        padding: EdgeInsets.all(16),
        color: Colors.grey.shade300, // لون أفتح لإشارة مكان العنصر الأصلي
        child: Text(
          item,
          style: TextStyle(fontSize: 30, color: Colors.grey),
        ),
      ),
      child: Container(
        padding: EdgeInsets.all(16),
        decoration: BoxDecoration(
          color: Theme.of(context).colorScheme.primary.withOpacity(0.8), // لون العنصر الأساسي
          borderRadius: BorderRadius.circular(10),
        ),
        child: Text(
          item,
          style: TextStyle(fontSize: 30, color: Colors.white),
        ),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('لعبة السحب والإفلات'),
        backgroundColor: Theme.of(context).appBarTheme.backgroundColor,
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [Theme.of(context).colorScheme.secondary.withOpacity(0.2),
            Colors.black.withOpacity(0.0), // شفاف في الأعلى
          ],
          begin: Alignment.topCenter,
          end: Alignment.bottomCenter,
          stops: [0.0, 0.5, 1.0],
        )),
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceAround,
            crossAxisAlignment: CrossAxisAlignment.center,
            children: [
              Text(
                'اسحب وأفلت العناصر في الفئات الصحيحة!',
                style: Theme.of(context).textTheme.headlineSmall?.copyWith(color: Theme.of(context).colorScheme.onBackground),
                textAlign: TextAlign.center,
              ),
              SizedBox(height: 20),
              // الفئات التي سيتم السحب إليها
              Expanded(
                flex: 2,
                child: GridView.builder(
                  shrinkWrap: true,
                  physics: NeverScrollableScrollPhysics(), // لمنع التمرير داخل الـ GridView
                  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                    crossAxisCount: 2, // فئتين في كل صف
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    childAspectRatio: 1.0, // نسبة العرض إلى الارتفاع لتبقى مربعة
                  ),
                  itemCount: categories.length,
                  itemBuilder: (context, index) {
                    final category = categories[index];
                    return _buildDropTarget(category);
                  },
                ),
              ),
              SizedBox(height: 30),
              Text(
                'عناصر التصنيف:',
                style: Theme.of(context).textTheme.titleLarge?.copyWith(color: Theme.of(context).colorScheme.onBackground),
              ),
              SizedBox(height: 10),
              // العناصر التي سيتم سحبها
              Expanded(
                flex: 1, // تأخذ مساحة أقل
                child: Wrap(
                  spacing: 12.0, // مسافة أفقية
                  runSpacing: 12.0, // مسافة عمودية
                  alignment: WrapAlignment.center, // توسيط العناصر
                  children: items.map((item) {
                    return _buildDraggableItem(item);
                  }).toList(),
                ),
              ),
              SizedBox(height: 30),
              // زر للتحقق من الإجابة
              ElevatedButton.icon(
                onPressed: _checkAndShowResult,
                icon: Icon(Icons.check),
                label: Text('تحقق من الإجابة'),
                style: ElevatedButton.styleFrom(
                  padding: EdgeInsets.symmetric(horizontal: 30, vertical: 15),
                  shape: RoundedRectangleBorder(
                    borderRadius: BorderRadius.circular(30),
                  ),
                  backgroundColor: Theme.of(context).colorScheme.secondary,
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}



---




#### `lib/screens/educational_games/memory_game_page.dart`

```dart
import 'package:flutter/material.dart';
import 'dart:async';
import 'dart:math';

class MemoryGamePage extends StatefulWidget {
  const MemoryGamePage({Key? key}) : super(key: key);

  @override
  _MemoryGamePageState createState() => _MemoryGamePageState();
}

class _MemoryGamePageState extends State<MemoryGamePage> {
  // قائمة الرموز التي سيتم استخدامها، يجب أن تكون متطابقة في أزواج
  List<String> _baseEmojis = [
    '🍎', '🐶', '🚗', '🌼', '🎈', '🦋', '⭐', '🌳', // أضف المزيد للحصول على لوحة أكبر
    '🎵', '🏠', '🚀', '❤️', '🌈', '🚲',
  ];
  late List<String> _gameEmojis; // الرموز الفعلية المستخدمة في اللعبة
  late List<bool> _revealed; // حالة إظهار/إخفاء كل بطاقة
  List<int> _selectedIndexes = []; // مؤشرات البطاقات المفتوحة حاليًا
  int _matchedPairs = 0; // عدد الأزواج المتطابقة
  bool _isBusy = false; // لمنع النقر أثناء فحص التطابق

  @override
  void initState() {
    super.initState();
    _startGame();
  }

  void _startGame() {
    setState(() {
      _gameEmojis = [];
      // اختر عدد معين من الأزواج
      int numberOfPairs = 8; // يمكنك تغيير هذا لزيادة/تقليل الصعوبة
      if (numberOfPairs > _baseEmojis.length) {
        numberOfPairs = _baseEmojis.length; // لا تتجاوز عدد الرموز الأساسية
      }

      // قم بإنشاء قائمة الألعاب مع الأزواج
      _gameEmojis.addAll(_baseEmojis.sublist(0, numberOfPairs));
      _gameEmojis.addAll(_baseEmojis.sublist(0, numberOfPairs));
      _gameEmojis.shuffle(Random()); // خلط الرموز
      
      _revealed = List<bool>.filled(_gameEmojis.length, false);
      _selectedIndexes.clear();
      _matchedPairs = 0;
      _isBusy = false;
    });
  }

  void _onTileTap(int index) {
    // تجاهل النقرات إذا كانت البطاقة مكشوفة بالفعل، أو كانت اللعبة مشغولة
    if (_revealed[index] || _isBusy) return;

    setState(() {
      _revealed[index] = true;
      _selectedIndexes.add(index);
    });

    if (_selectedIndexes.length == 2) {
      _isBusy = true; // منع النقر أثناء فحص التطابق
      Future.delayed(Duration(milliseconds: 700), () { // تقليل وقت التأخير قليلاً
        setState(() {
          int first = _selectedIndexes[0];
          int second = _selectedIndexes[1];
          if (_gameEmojis[first] == _gameEmojis[second]) {
            _matchedPairs++;
          } else {
            _revealed[first] = false;
            _revealed[second] = false;
          }
          _selectedIndexes.clear();
          _isBusy = false;
        });
        if (_matchedPairs == _gameEmojis.length ~/ 2) {
          _showWinDialog();
        }
      });
    }
  }

  void _showWinDialog() {
    showDialog(
      context: context,
      barrierDismissible: false, // لا يمكن إغلاقها بالنقر خارجها
      builder: (context) {
        return AlertDialog(
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20)),
          title: Text(
            'تهانينا!',
            textAlign: TextAlign.center,
            style: TextStyle(fontWeight: FontWeight.bold, color: Theme.of(context).primaryColor),
          ),
          content: Text(
            'لقد طابقت جميع الأزواج بنجاح!',
            textAlign: TextAlign.center,
            style: TextStyle(fontSize: 16),
          ),
          actionsAlignment: MainAxisAlignment.center,
          actions: [
            ElevatedButton(
              onPressed: () {
                Navigator.of(context).pop();
                _startGame();
              },
              style: ElevatedButton.styleFrom(
                backgroundColor: Theme.of(context).colorScheme.secondary,
                shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
                padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10)
              ),
              child: Text("العب مرة أخرى"),
            ),
            TextButton(
              onPressed: () {
                Navigator.of(context).pop();
                Navigator.of(context).pop(); // العودة إلى شاشة الألعاب
              },
              child: Text("أعود للقائمة"),
              style: TextButton.styleFrom(
                foregroundColor: Colors.grey.shade600
              ),
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: const Text('لعبة الذاكرة - الأوراق المتطابقة'),
        backgroundColor: theme.appBarTheme.backgroundColor,
        centerTitle: true,
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [theme.colorScheme.tertiary.withOpacity(0.3), theme.colorScheme.background],
            begin: Alignment.topLeft,
            end: Alignment.bottomRight,
          ),
        ),
        padding: const EdgeInsets.all(12.0),
        child: GridView.builder(
          itemCount: _gameEmojis.length,
          gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
            crossAxisCount: 4, // زيادة الأعمدة لتبدو أكثر كلعبة ذاكرة
            crossAxisSpacing: 8,
            mainAxisSpacing: 8,
            childAspectRatio: 0.9, // لجعل البطاقات مستطيلة قليلاً
          ),
          itemBuilder: (context, index) {
            return GestureDetector(
              onTap: () => _onTileTap(index),
              child: AnimatedContainer(
                duration: Duration(milliseconds: 300),
                decoration: BoxDecoration(
                  color: _revealed[index] ? Colors.white : Colors.purple.shade200, // لون أفتح للجانب الخلفي
                  borderRadius: BorderRadius.circular(12),
                  border: Border.all(
                    color: _revealed[index] ? theme.colorScheme.primary : Colors.purple.shade400,
                    width: 2,
                  ),
                  boxShadow: [
                    BoxShadow(
                      color: Colors.black.withOpacity(0.15),
                      blurRadius: 5,
                      offset: Offset(2, 3),
                    ),
                  ],
                ),
                child: Center(
                  child: Text(
                    _revealed[index] ? _gameEmojis[index] : '❓', // رمز السؤال كالجزء الخلفي
                    style: TextStyle(fontSize: 36), // حجم أكبر للأيقونات
                  ),
                ),
              ),
            );
          },
        ),
      ),
    );
  }
}
```

#### `lib/screens/educational_games/maze_game.dart`

```dart
import 'package:flutter/material.dart';
import 'dart:async';

class MazeGame extends StatefulWidget {
  @override
  _MazeGameState createState() => _MazeGameState();
}

class _MazeGameState extends State<MazeGame> {
  // تمثيل المتاهة (1 = مفتوح، 0 = مغلق)
  List<List<int>> maze = [
    [1, 1, 1, 0, 1],
    [0, 1, 1, 0, 1], // تم تعديل المسار لجعل اللعبة قابلة للحل أكثر
    [1, 1, 1, 1, 1],
    [1, 0, 0, 1, 1],
    [1, 1, 1, 1, 1]
  ];

  int playerX = 0, playerY = 0; // الموقع الحالي للاعب (البداية)
  Timer? timer;
  int seconds = 0;
  bool _gameStarted = false; // لضمان أن المؤقت يبدأ فقط عند أول حركة أو النقر على "بدء"
  bool _gameWon = false;

  // تحديد موقع النهاية في المتاهة
  final int endX = 4;
  final int endY = 4;

  @override
  void initState() {
    super.initState();
    _resetGame();
  }

  void _resetGame() {
    setState(() {
      playerX = 0;
      playerY = 0;
      seconds = 0;
      _gameStarted = false;
      _gameWon = false;
    });
    timer?.cancel();
  }

  void _startGameTimer() {
    if (!_gameStarted) {
      _gameStarted = true;
      timer = Timer.periodic(Duration(seconds: 1), (Timer t) {
        if (!_gameWon) {
          setState(() {
            seconds++;
          });
        }
      });
    }
  }

  void movePlayer(int dx, int dy) {
    if (_gameWon) return; // لا تسمح بالحركة بعد الفوز

    _startGameTimer(); // بدء المؤقت عند أول حركة

    int newX = playerX + dx;
    int newY = playerY + dy;

    if (newX >= 0 && newX < maze.length && newY >= 0 && newY < maze[0].length && maze[newX][newY] == 1) {
      setState(() {
        playerX = newX;
        playerY = newY;
      });
    }

    // إذا وصل اللاعب إلى النهاية
    if (playerX == endX && playerY == endY) {
      _gameWon = true;
      timer?.cancel();
      _showWinDialog();
    }
  }

  void _showWinDialog() {
    showDialog(
      context: context,
      barrierDismissible: false,
      builder: (context) {
        return AlertDialog(
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20)),
          title: Text('تهانينا!', textAlign: TextAlign.center, style: TextStyle(fontWeight: FontWeight.bold, color: Theme.of(context).primaryColor)),
          content: Text(
            'لقد نجحت في الهروب من المتاهة في $seconds ثانية!',
            textAlign: TextAlign.center,
            style: TextStyle(fontSize: 16),
          ),
          actionsAlignment: MainAxisAlignment.center,
          actions: [
            ElevatedButton(
              onPressed: () {
                Navigator.of(context).pop();
                _resetGame();
              },
              style: ElevatedButton.styleFrom(
                backgroundColor: Theme.of(context).colorScheme.secondary,
                shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
                padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10)
              ),
              child: Text('إعادة اللعبة'),
            ),
            TextButton(
              onPressed: () {
                Navigator.of(context).pop();
                Navigator.of(context).pop(); // العودة إلى شاشة الألعاب
              },
              child: Text("أعود للقائمة"),
              style: TextButton.styleFrom(
                foregroundColor: Colors.grey.shade600
              ),
            ),
          ],
        );
      },
    );
  }

  @override
  void dispose() {
    timer?.cancel();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    return Scaffold(
      appBar: AppBar(
        title: Text('لعبة الهروب من المتاهة'),
        backgroundColor: theme.appBarTheme.backgroundColor,
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [theme.colorScheme.primary.withOpacity(0.3), theme.colorScheme.background],
            begin: Alignment.topLeft,
            end: Alignment.bottomRight,
          ),
        ),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Padding(
              padding: const EdgeInsets.all(20.0),
              child: Text(
                'الوصول إلى العلم الأخضر قبل نفاذ الوقت!',
                style: theme.textTheme.titleLarge?.copyWith(color: theme.colorScheme.onBackground),
                textAlign: TextAlign.center,
              ),
            ),
            Center(
              child: Container(
                height: 300,
                width: 300,
                decoration: BoxDecoration(
                  border: Border.all(color: Colors.grey.shade600, width: 2),
                  borderRadius: BorderRadius.circular(10),
                ),
                child: GridView.builder(
                  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                    crossAxisCount: maze[0].length,
                    crossAxisSpacing: 1.0,
                    mainAxisSpacing: 1.0,
                  ),
                  itemCount: maze.length * maze[0].length,
                  itemBuilder: (context, index) {
                    int x = index ~/ maze[0].length;
                    int y = index % maze[0].length;
                    bool isPlayer = x == playerX && y == playerY;
                    bool isStart = x == 0 && y == 0;
                    bool isEnd = x == endX && y == endY;

                    Color tileColor;
                    Widget? content;

                    if (maze[x][y] == 0) {
                      tileColor = Colors.grey.shade800; // الجدار (لون داكن)
                    } else if (isPlayer) {
                      tileColor = theme.colorScheme.primary; // لون اللاعب
                      content = Icon(Icons.directions_run_rounded, color: Colors.white, size: 30);
                    } else if (isEnd) {
                      tileColor = Colors.green.shade700; // لون النهاية
                      content = Icon(Icons.flag, color: Colors.white, size: 30);
                    } else if (isStart) {
                      tileColor = Colors.blue.shade700; // لون البداية
                      content = Icon(Icons.play_arrow_rounded, color: Colors.white, size: 30);
                    }
                    else {
                      tileColor = Colors.white; // المسار المفتوح
                    }

                    return AnimatedContainer(
                      duration: Duration(milliseconds: 200),
                      color: tileColor,
                      child: Center(child: content),
                    );
                  },
                ),
              ),
            ),
            SizedBox(height: 30),
            Text(
              'الوقت: $seconds ثواني',
              style: theme.textTheme.headlineSmall?.copyWith(color: theme.colorScheme.onBackground),
            ),
            SizedBox(height: 30),
            Container(
              decoration: BoxDecoration(
                color: theme.cardTheme.color,
                borderRadius: BorderRadius.circular(15),
                boxShadow: [
                  BoxShadow(
                    color: Colors.black.withOpacity(0.1),
                    blurRadius: 10,
                    spreadRadius: 2,
                  )
                ]
              ),
              padding: EdgeInsets.all(20),
              child: Column(
                children: [
                  IconButton(
                    icon: Icon(Icons.arrow_circle_up, size: 50, color: Colors.blue.shade700),
                    onPressed: () => movePlayer(-1, 0),
                    tooltip: 'Up',
                  ),
                  Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      IconButton(
                        icon: Icon(Icons.arrow_circle_left, size: 50, color: Colors.blue.shade700),
                        onPressed: () => movePlayer(0, -1),
                        tooltip: 'Left',
                      ),
                      SizedBox(width: 60), // لترك مسافة بين أزرار الاتجاهات
                      IconButton(
                        icon: Icon(Icons.arrow_circle_right, size: 50, color: Colors.blue.shade700),
                        onPressed: () => movePlayer(0, 1),
                        tooltip: 'Right',
                      ),
                    ],
                  ),
                  IconButton(
                    icon: Icon(Icons.arrow_circle_down, size: 50, color: Colors.blue.shade700),
                    onPressed: () => movePlayer(1, 0),
                    tooltip: 'Down',
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

#### `lib/screens/messaging/compose_message_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart'; // لاستخدام التاريخ في اقتباس الرد
import 'package:kids/screens/messaging/gmail_inbox_screen.dart'; // <--- تأكد من صحة المسار لنموذج Email

class ComposeMessageScreen extends StatefulWidget {
  final Email? replyToEmail;
  final bool replyAll;
  final Email? forwardEmail;

  const ComposeMessageScreen({
    Key? key,
    this.replyToEmail,
    this.replyAll = false,
    this.forwardEmail,
  }) : super(key: key);

  @override
  _ComposeMessageScreenState createState() => _ComposeMessageScreenState();
}

class _ComposeMessageScreenState extends State<ComposeMessageScreen> {
  final _formKey = GlobalKey<FormState>();
  String? _selectedRecipient;
  final _subjectController = TextEditingController();
  final _messageController = TextEditingController();

  final List<String> _recipients = [
    'المعلمة فاطمة',
    'الإدارة المدرسية',
    'المشرفة التربوية',
    'قسم الدعم',
  ];

  String _appBarTitle = 'إنشاء رسالة جديدة';

  @override
  void initState() {
    super.initState();
    _appBarTitle = _getAppBarTitle();

    if (widget.replyToEmail != null) {
      String originalSubject = widget.replyToEmail!.subject;
      if (!originalSubject.toLowerCase().startsWith('re: ')) {
         _subjectController.text = 'Re: $originalSubject';
      } else {
         _subjectController.text = originalSubject;
      }

      String formattedDate = DateFormat('EEEE, MMMM d, yyyy, hh:mm a', 'ar').format(widget.replyToEmail!.timestamp);
      String quoteHeader = '\n\n--- في $formattedDate، كتب ${widget.replyToEmail!.sender} <${widget.replyToEmail!.senderEmail}>: ---\n';
      String originalBody = widget.replyToEmail!.body.split('\n').map((line) => '> $line').join('\n');
      _messageController.text = quoteHeader + originalBody;
      _messageController.selection = TextSelection.fromPosition(TextPosition(offset: 0));

    } else if (widget.forwardEmail != null) {
       String originalSubject = widget.forwardEmail!.subject;
      if (!originalSubject.toLowerCase().startsWith('fwd: ')) {
         _subjectController.text = 'Fwd: $originalSubject';
      } else {
         _subjectController.text = originalSubject;
      }

       String formattedDate = DateFormat('EEEE, MMMM d, yyyy, hh:mm a', 'ar').format(widget.forwardEmail!.timestamp);
       String forwardHeader = '\n\n---------- رسالة محولة ----------\n'
                              'من: ${widget.forwardEmail!.sender} <${widget.forwardEmail!.senderEmail}>\n'
                              'التاريخ: $formattedDate\n'
                              'الموضوع: ${widget.forwardEmail!.subject}\n'
                              'إلى: ${widget.forwardEmail!.recipientsTo.join(', ')}\n';
       if (widget.forwardEmail!.recipientsCc != null && widget.forwardEmail!.recipientsCc!.isNotEmpty) {
         forwardHeader += 'نسخة إلى: ${widget.forwardEmail!.recipientsCc!.join(', ')}\n';
       }
       forwardHeader += '\n';
       _messageController.text = forwardHeader + widget.forwardEmail!.body;
       _messageController.selection = TextSelection.fromPosition(TextPosition(offset: 0));
    }
  }

  @override
  void dispose() {
    _subjectController.dispose();
    _messageController.dispose();
    super.dispose();
  }

  void _sendMessage() {
     if (_formKey.currentState!.validate()) {
       _formKey.currentState!.save();
       final recipient = _selectedRecipient;
       final subject = _subjectController.text;
       final message = _messageController.text;

       ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(
          content: Text('جاري الإرسال إلى ($recipient)...'),
          backgroundColor: Colors.green,
          duration: Duration(seconds: 2),
        ),
      );
       Navigator.of(context).pop();

     } else {
        ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(
            content: Text('الرجاء تعبئة الحقول المطلوبة واختيار مستلم.'),
            backgroundColor: Colors.red,
          ),
        );
     }
  }

  String _getAppBarTitle() {
    if (widget.replyToEmail != null) {
      return widget.replyAll ? 'رد على الكل' : 'رد';
    } else if (widget.forwardEmail != null) {
      return 'إعادة توجيه';
    } else {
      return 'إنشاء رسالة جديدة';
    }
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);

    return Scaffold(
      appBar: AppBar(
        title: Text(_appBarTitle),
        elevation: 1.0,
        actions: [
           IconButton(
             icon: Icon(Icons.send),
             tooltip: 'إرسال', // Tooltip بالعربية
             onPressed: _sendMessage,
           )
        ],
      ),
      body: Form(
        key: _formKey,
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          // Column aligns children to the start (right in RTL) by default
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start, // RTL alignment for start
            children: [
              Text(
                'إلى *',
                style: theme.textTheme.titleSmall?.copyWith(
                  fontWeight: FontWeight.bold,
                  color: theme.colorScheme.onSurface.withOpacity(0.8),
                ),
              ),
              const SizedBox(height: 8.0),
              DropdownButtonFormField<String>(
                value: _selectedRecipient,
                hint: const Text('-- اختر المستلم --'),
                isExpanded: true,
                decoration: InputDecoration(
                   border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(8.0),
                  ),
                  contentPadding: const EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                ),
                items: _recipients.map((String recipient) {
                  return DropdownMenuItem<String>(
                    value: recipient,
                    child: Text(recipient, textAlign: TextAlign.right), // Force text direction for dropdown items
                  );
                }).toList(),
                onChanged: (String? newValue) {
                  setState(() {
                    _selectedRecipient = newValue;
                  });
                },
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'الرجاء اختيار مستلم للرسالة';
                  }
                  return null;
                },
              ),
              const SizedBox(height: 20.0),

              Text(
                'الموضوع',
                 style: theme.textTheme.titleSmall?.copyWith(
                   fontWeight: FontWeight.bold,
                  color: theme.colorScheme.onSurface.withOpacity(0.8),
                 ),
               ),
               const SizedBox(height: 8.0),
              TextFormField(
                controller: _subjectController,
                decoration: InputDecoration(
                   hintText: 'أدخل موضوع الرسالة هنا',
                   border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(8.0),
                  ),
                   contentPadding: const EdgeInsets.symmetric(horizontal: 12.0, vertical: 15.0),
                ),
                textInputAction: TextInputAction.next,
                textAlign: TextAlign.right, // Align text to right in RTL
              ),
              const SizedBox(height: 20.0),

              Text(
                'نص الرسالة *',
                style: theme.textTheme.titleSmall?.copyWith(
                   fontWeight: FontWeight.bold,
                  color: theme.colorScheme.onSurface.withOpacity(0.8),
                ),
              ),
              const SizedBox(height: 8.0),
              TextFormField(
                controller: _messageController,
                decoration: InputDecoration(
                   hintText: 'اكتب محتوى رسالتك هنا...',
                   border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(8.0),
                  ),
                  alignLabelWithHint: true,
                  contentPadding: const EdgeInsets.symmetric(horizontal: 12.0, vertical: 15.0),
                ),
                maxLines: 15,
                minLines: 10,
                keyboardType: TextInputType.multiline,
                textAlign: TextAlign.right, // Align text to right in RTL
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'الرجاء كتابة نص للرسالة';
                  }
                  return null;
                },
              ),
              const SizedBox(height: 24.0),
            ],
          ),
        ),
      ),
    );
  }
}
```

#### `lib/screens/messaging/email_detail_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';
import 'package:kids/screens/messaging/gmail_inbox_screen.dart'; // <--- تأكد من صحة المسار لنموذج Email
import 'package:kids/screens/messaging/compose_message_screen.dart'; // <--- تأكد من صحة المسار

class EmailDetailScreen extends StatefulWidget {
  final Email email;

  const EmailDetailScreen({Key? key, required this.email}) : super(key: key);

  @override
  _EmailDetailScreenState createState() => _EmailDetailScreenState();
}

class _EmailDetailScreenState extends State<EmailDetailScreen> {
  bool _showRecipientDetails = false;

  String _formatDetailedTimestamp(DateTime timestamp) {
    return DateFormat('EEEE, MMMM d, yyyy, hh:mm a', 'ar').format(timestamp); // تنسيق عربي
  }

  Color _getAvatarColor(String letter) {
    final colors = [Colors.red, Colors.blue, Colors.green, Colors.orange, Colors.purple, Colors.teal, Colors.brown];
    final index = letter.toUpperCase().codeUnitAt(0) % colors.length;
    return colors[index].shade300;
  }

  void _toggleStar() {
    setState(() {
      widget.email.isStarred = !widget.email.isStarred;
    });
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(content: Text(widget.email.isStarred ? 'تم تمييز الرسالة بنجمة' : 'تم إزالة النجمة من الرسالة'))
    );
  }

  String _formatSimpleTimestamp(DateTime timestamp) {
    final now = DateTime.now();
    final difference = now.difference(timestamp);
    if (difference.inDays == 0 && now.day == timestamp.day) return DateFormat.jm('ar').format(timestamp);
    if (difference.inDays == 1 || (difference.inDays == 0 && now.day != timestamp.day)) return 'أمس'; // Yesterday in Arabic
    if (difference.inDays < 7) return DateFormat.E('ar').format(timestamp);
    return DateFormat('dd MMM', 'ar').format(timestamp); // dd MMM in Arabic
  }

  Widget _buildDetailRow(String label, String value) {
    return Padding(
      padding: const EdgeInsets.only(bottom: 4.0),
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Text(label, style: TextStyle(color: Colors.grey.shade600, fontSize: 13)),
          SizedBox(width: 8),
          Expanded(child: SelectableText(value, style: TextStyle(fontSize: 13), textAlign: TextAlign.start)),
        ],
      ),
    );
  }

  Widget _buildReplyButton(BuildContext context, IconData icon, String label, VoidCallback onPressed) {
    return TextButton.icon(
      icon: Icon(icon, size: 20),
      label: Text(label),
      onPressed: onPressed,
      style: TextButton.styleFrom(
        padding: EdgeInsets.symmetric(horizontal: 12, vertical: 8),
        foregroundColor: Theme.of(context).colorScheme.primary,
         shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(20.0)),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    final textTheme = theme.textTheme;
    final email = widget.email;

    return Scaffold(
      appBar: AppBar(
         backgroundColor: theme.scaffoldBackgroundColor,
         foregroundColor: theme.iconTheme.color,
         elevation: 0.5,
        actions: [
           IconButton(
            tooltip: email.isStarred ? 'إلغاء النجمة' : 'تمييز بنجمة',
            icon: Icon(
              email.isStarred ? Icons.star : Icons.star_border,
              color: email.isStarred ? Colors.amber.shade700 : null,
            ),
            onPressed: _toggleStar,
          ),
          IconButton(tooltip: 'أرشفة', icon: Icon(Icons.archive_outlined), onPressed: () {ScaffoldMessenger.of(context).showSnackBar(SnackBar(content: Text('وظيفة الأرشفة قريباً')));}),
          IconButton(tooltip: 'حذف', icon: Icon(Icons.delete_outline), onPressed: () {ScaffoldMessenger.of(context).showSnackBar(SnackBar(content: Text('وظيفة الحذف قريباً')));}),
          IconButton(tooltip: 'تمييز كغير مقروء', icon: Icon(Icons.mark_email_unread_outlined), onPressed: () {ScaffoldMessenger.of(context).showSnackBar(SnackBar(content: Text('وظيفة تمييز كغير مقروء قريباً')));}),

          PopupMenuButton<String>(
            tooltip: 'المزيد من الخيارات',
            icon: Icon(Icons.more_vert_outlined),
            onSelected: (String result) {
              ScaffoldMessenger.of(context).showSnackBar(
                SnackBar(content: Text('تم اختيار: $result')),
              );
            },
            itemBuilder: (BuildContext context) => <PopupMenuEntry<String>>[
              const PopupMenuItem<String>(value: 'move', child: Text('نقل إلى...')),
              const PopupMenuItem<String>(value: 'snooze', child: Text('تأجيل')),
              const PopupMenuItem<String>(value: 'change_labels', child: Text('تغيير التصنيفات')),
              const PopupMenuItem<String>(value: 'mute', child: Text('كتم')),
              const PopupMenuItem<String>(value: 'print', child: Text('طباعة')),
              const PopupMenuItem<String>(value: 'spam', child: Text('الإبلاغ عن رسائل مزعجة')),
              PopupMenuItem<String>(value: 'block', child: Text('حظر "${widget.email.sender}"')),
            ],
          ),
        ],
      ),
      body: ListView(
        padding: const EdgeInsets.fromLTRB(16.0, 8.0, 16.0, 80.0), // زيادة مسافة الأيقونات في الأسفل
        children: [
             // --- Subject ---
          Padding(
            padding: const EdgeInsets.only(bottom: 16.0, top: 8.0),
            child: Text(
              email.subject.isEmpty ? '(لا يوجد موضوع)' : email.subject, // نص عربي
              style: textTheme.headlineSmall?.copyWith(fontWeight: FontWeight.normal, fontSize: 22),
              textAlign: TextAlign.start,
            ),
          ),

          // --- Sender/Recipient Info (Expandable) ---
           InkWell(
            onTap: () {
              setState(() {
                _showRecipientDetails = !_showRecipientDetails;
              });
            },
             child: Padding(
               padding: const EdgeInsets.symmetric(vertical: 8.0),
               child: Row(
                 crossAxisAlignment: CrossAxisAlignment.start,
                 children: [
                    // Avatar
                    CircleAvatar(
                      radius: 22,
                      backgroundColor: _getAvatarColor(email.avatarLetter),
                      child: Text(email.avatarLetter.toUpperCase(), style: TextStyle(fontSize: 18, color: Colors.white, fontWeight: FontWeight.bold)),
                    ),
                    const SizedBox(width: 12.0),
                    // Details Column
                    Expanded(
                      child: Column(
                       crossAxisAlignment: CrossAxisAlignment.start,
                       children: [
                          // Sender and Time Row
                          Row(
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: [
                              Expanded(child: Text(email.sender, style: textTheme.titleMedium?.copyWith(fontWeight: FontWeight.w500), maxLines: 1, overflow: TextOverflow.ellipsis, textAlign: TextAlign.start)),
                              SizedBox(width: 8),
                              Text(_formatSimpleTimestamp(email.timestamp), style: textTheme.bodySmall),
                            ],
                          ),
                          SizedBox(height: 2),
                          // Recipient Row (Expandable)
                          Row(
                            children: [
                              Text('إلى ${ _showRecipientDetails ? "أنا" : (email.recipientsTo.isNotEmpty ? email.recipientsTo.first.split('<')[0].trim() : "غير معروف") }', style: textTheme.bodySmall?.copyWith(color: Colors.grey.shade600), overflow: TextOverflow.ellipsis, textAlign: TextAlign.start), // نص عربي
                              Icon(_showRecipientDetails ? Icons.keyboard_arrow_up : Icons.keyboard_arrow_down, size: 18, color: Colors.grey.shade600),
                            ],
                          ),
                          // Expanded Details
                          if (_showRecipientDetails)
                           Padding(
                             padding: const EdgeInsets.only(top: 8.0),
                             child: Column(
                              crossAxisAlignment: CrossAxisAlignment.start,
                              children: [
                                _buildDetailRow('من:', email.senderEmail), // نص عربي
                                _buildDetailRow('إلى:', email.recipientsTo.join(', ')), // نص عربي
                                if (email.recipientsCc != null && email.recipientsCc!.isNotEmpty) _buildDetailRow('نسخة إلى:', email.recipientsCc!.join(', ')), // نص عربي
                                _buildDetailRow('التاريخ:', _formatDetailedTimestamp(email.timestamp)), // نص عربي
                              ],
                             ),
                           )
                       ],
                     ),
                    ),
                    // Attachment Icon
                    if (email.hasAttachment) Padding(padding: const EdgeInsets.only(top: 4.0, right: 8.0), child: Icon(Icons.attachment_outlined, color: Colors.grey.shade600)),
                 ],
               ),
             ),
           ),
           Divider(height: 24),

          // --- Message Body ---
          Padding(
            padding: const EdgeInsets.symmetric(vertical: 12.0),
            child: SelectableText(
              email.body,
              style: textTheme.bodyLarge?.copyWith(height: 1.6, fontSize: 15),
              textAlign: TextAlign.start,
            ),
          ),
        ],
      ),

       // --- Reply Buttons (Fixed at bottom) ---
       bottomSheet: Container(
          padding: EdgeInsets.symmetric(vertical: 10.0, horizontal: 16.0),
          decoration: BoxDecoration(
             color: theme.cardColor,
             border: Border(top: BorderSide(color: Colors.grey.shade300, width: 0.5)),
           ),
         child: Row(
           mainAxisAlignment: MainAxisAlignment.spaceAround,
           children: [
             _buildReplyButton(context, Icons.reply_outlined, 'رد', () { // نص عربي
                Navigator.push(context, MaterialPageRoute(builder: (context) => ComposeMessageScreen(replyToEmail: email)));
             }),
             _buildReplyButton(context, Icons.reply_all_outlined, 'رد على الكل', () { // نص عربي
                Navigator.push(context, MaterialPageRoute(builder: (context) => ComposeMessageScreen(replyToEmail: email, replyAll: true)));
             }),
             _buildReplyButton(context, Icons.forward_outlined, 'إعادة توجيه', () { // نص عربي
                 Navigator.push(context, MaterialPageRoute(builder: (context) => ComposeMessageScreen(forwardEmail: email)));
             }),
           ],
         ),
       ),
    );
  }
}
```

#### `lib/screens/messaging/gmail_inbox_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart'; // لإدارة تنسيق الوقت
import 'package:kids/screens/messaging/email_detail_screen.dart'; // استورد شاشة التفاصيل
import 'package:kids/screens/messaging/compose_message_screen.dart'; // استورد شاشة الإنشاء


// نموذج بيانات للرسالة (مُعدّل ليتوافق مع LTR ولـ Gmail Inbox)
class Email {
  final String sender;
  final String senderEmail;
  final String avatarLetter;
  final String subject;
  final String preview;
  final String body;
  final List<String> recipientsTo;
  final List<String>? recipientsCc;
  final DateTime timestamp;
  bool isUnread; // لم تعد final لكي يمكن تغييرها
  bool isStarred; // لم تعد final لكي يمكن تغييرها
  final bool hasAttachment;

  Email({
    required this.sender,
    required this.senderEmail,
    required this.avatarLetter,
    required this.subject,
    required this.preview,
    required this.body,
    required this.recipientsTo,
    this.recipientsCc,
    required this.timestamp,
    this.isUnread = false,
    this.isStarred = false,
    this.hasAttachment = false,
  });
}


class GmailInboxScreen extends StatefulWidget {
  const GmailInboxScreen({Key? key}) : super(key: key);

  @override
  _GmailInboxScreenState createState() => _GmailInboxScreenState();
}

class _GmailInboxScreenState extends State<GmailInboxScreen> {
  // قائمة وهمية بالرسائل
  final List<Email> emails = [
      Email(
        sender: 'مدير النظام',
        senderEmail: 'admin@kindergarten.com',
        avatarLetter: 'م',
        subject: 'إعلان: حفل نهاية العام الدراسي',
        preview: 'يسرنا دعوتكم لحفل نهاية العام الدراسي، تفضلوا بقراءة التفاصيل...',
        body: 'أهلاً بكم أولياء الأمور الأعزاء،\n\nيسعدنا دعوتكم لحفل نهاية العام الدراسي والذي سيقام في تاريخ 2025-06-15 الساعة 10 صباحًا. يرجى تأكيد حضوركم قبل تاريخ 2025-06-01.\n\nنتطلع لرؤيتكم هناك!\n\nمع خالص الشكر,\nإدارة الروضة',
        recipientsTo: ['أولياء الأمور <parents@kindergarten.com>'],
        timestamp: DateTime.now().subtract(Duration(minutes: 15)),
        isUnread: true, isStarred: false, hasAttachment: true
    ),
    Email(
        sender: 'المعلمة سارة',
        senderEmail: 'sarah.teacher@kindergarten.com',
        avatarLetter: 'س',
        subject: 'ملاحظة حول تقدم أحمد في القراءة',
        preview: 'أردت إعلامكم بتقدم أحمد المميز هذا الأسبوع في أنشطة القراءة...',
        body: 'صباح الخير ولي الأمر الكريم,\n\nأردت إعلامكم بتقدم أحمد المميز هذا الأسبوع في أنشطة القراءة. لقد أصبح يتعرف على المزيد من الحروف وبدأ في ربطها لتكوين كلمات بسيطة.\n\nاستمروا في تشجيعه في المنزل!\n\nتحياتي,\nالمعلمة سارة',
        recipientsTo: ['ولي أمر أحمد <parent1@example.com>'],
        timestamp: DateTime.now().subtract(Duration(hours: 2)),
        isUnread: true, isStarred: true
    ),
    Email(
        sender: 'قسم الدعم',
        senderEmail: 'support@kindergarten.com',
        avatarLetter: 'د',
        subject: 'تم حل مشكلتك: لا توجد مشكلة بالوصول للصور',
        preview: 'بالإشارة إلى استفساركم بخصوص الوصول لصور المعرض، تم حل المشكلة الآن...',
        body: 'تحية طيبة،\n\nبخصوص استفساركم عن عدم القدرة على رؤية صور المعرض، نود إبلاغكم بأن المشكلة تم حلها الآن. يرجى المحاولة مرة أخرى.\n\nنعتذر عن أي إزعاج.\n\nفريق الدعم الفني',
        recipientsTo: ['أحمد ولي الأمر <parent1@example.com>'],
        recipientsCc: ['مدير <admin@kindergarten.com>'],
        timestamp: DateTime.now().subtract(Duration(days: 1)),
        hasAttachment: false
     ),
     Email(
        sender: 'إدارة الروضة',
        senderEmail: 'info@kindergarten.com',
        avatarLetter: 'إ',
        subject: 'تذكير: لقاحات شهر مايو',
        preview: 'يرجى العلم بضرورة مراجعة السجل الصحي للطفل والتأكد من تحديث لقاحاته...',
        body: 'أولياء الأمور الأعزاء,\n\nهذا تذكير بأهمية تحديث لقاحات أطفالكم. يرجى مراجعة سجلات طفلكم الصحية والتأكد من أن جميع اللقاحات في موعدها.\n\nلمزيد من المعلومات يرجى التواصل مع قسم الصحة.\n\nمع فائق الاحترام,\nإدارة الروضة',
        recipientsTo: ['جميع أولياء الأمور <allparents@kindergarten.com>'],
        timestamp: DateTime.now().subtract(Duration(days: 2, hours: 5)),
        isUnread: false, isStarred: false
     ),
  ];

  // دالة لتنسيق الوقت بشكل مشابه لـ Gmail (RTL example)
  String _formatTimestamp(DateTime timestamp) {
    final now = DateTime.now();
    final difference = now.difference(timestamp);

    if (difference.inDays == 0 && now.day == timestamp.day) {
      return DateFormat.jm('ar').format(timestamp); // مثال: ٩:٠٠ ص
    } else if (difference.inDays == 1 || (difference.inDays == 0 && now.day != timestamp.day)) {
      return 'أمس'; // أمس
    } else if (difference.inDays < 7) {
       return DateFormat.E('ar').format(timestamp); // اسم اليوم مختصر (الأحد، الاثنين)
    } else {
      return DateFormat('dd/MM/yyyy', 'ar').format(timestamp); // تاريخ كامل (٢٠٢٤/٠٣/٢٠)
    }
  }

  // دالة لتوليد لون للخلفية بناءً على الحرف (تصلح لكلا الاتجاهين)
  Color _getAvatarColor(String letter) {
    final colors = [Colors.red, Colors.blue, Colors.green, Colors.orange, Colors.purple, Colors.teal, Colors.brown];
    final index = letter.toUpperCase().codeUnitAt(0) % colors.length;
    return colors[index].shade300;
  }

  Future<void> _refreshEmails() async {
    // محاكاة تحميل بيانات جديدة
    await Future.delayed(Duration(seconds: 1));
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text('تم تحديث البريد الوارد'),
        duration: Duration(seconds: 1),
      ),
    );
     // في تطبيق حقيقي، ستستدعي API هنا وتحديث حالة الـ emails
  }

  // دالة لتبديل حالة النجمة
  void _toggleStar(Email email) {
    setState(() {
      email.isStarred = !email.isStarred;
    });
     ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text(email.isStarred ? 'تم تمييز الرسالة بنجمة' : 'تم إزالة النجمة من الرسالة'),
        duration: Duration(seconds: 1),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);

    return Scaffold(
      appBar: AppBar(
        title: Text('صندوق الوارد'),
        actions: [
          IconButton(
            icon: Icon(Icons.search),
            tooltip: 'بحث',
            onPressed: () {
              ScaffoldMessenger.of(context).showSnackBar(
                SnackBar(content: Text('وظيفة البحث قريباً'))
              );
            },
          ),
          IconButton(
            icon: CircleAvatar(
              radius: 15,
              backgroundColor: Colors.grey.shade300,
              child: Icon(Icons.person_outline, size: 20, color: Colors.grey.shade700),
            ),
             tooltip: 'الحساب الشخصي',
            onPressed: () {
              ScaffoldMessenger.of(context).showSnackBar(
                SnackBar(content: Text('وظيفة الحساب الشخصي قريباً'))
              );
            },
          ),
          SizedBox(width: 8),
        ],
        elevation: 1.0,
      ),
      drawer: _buildDrawer(context), // القائمة الجانبية
      body: RefreshIndicator(
         onRefresh: _refreshEmails,
        child: ListView.builder(
          itemCount: emails.length,
          itemBuilder: (context, index) {
            final email = emails[index];
            return _buildEmailListItem(context, email, theme, _toggleStar);
          },
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
           // الانتقال إلى شاشة إنشاء رسالة جديدة
           Navigator.push(context, MaterialPageRoute(builder: (context) => ComposeMessageScreen()));
        },
        child: Icon(Icons.edit_outlined),
        tooltip: 'إنشاء رسالة',
      ),
    );
  }

 // ودجت بناء عنصر القائمة - يستقبل الآن دالة onStarTap
 Widget _buildEmailListItem(BuildContext context, Email email, ThemeData theme, Function(Email) onStarTap) {
    final bool isUnread = email.isUnread;
    final Color avatarColor = _getAvatarColor(email.avatarLetter);

    return InkWell(
      onTap: () {
        Navigator.push(
          context,
          MaterialPageRoute(
            builder: (context) => EmailDetailScreen(email: email),
          ),
        ).then((_) {
           // عندما نعود من شاشة التفاصيل، نحدث حالة الرسائل لتعكس أي تغييرات
           if (isUnread) {
             setState(() {
               email.isUnread = false; // تحديث حالة الرسالة كمقروءة
             });
           }
        });
      },
      child: Padding(
        padding: const EdgeInsets.only(top: 4.0, bottom: 4.0, left: 12.0, right: 4.0),
        child: Row(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // --- Avatar ---
            Padding(
              padding: const EdgeInsets.only(top: 8.0, right: 4.0),
              child: CircleAvatar(
                radius: 22,
                backgroundColor: avatarColor,
                child: Text(
                  email.avatarLetter.toUpperCase(),
                  style: TextStyle(fontSize: 18, color: Colors.white, fontWeight: FontWeight.bold),
                ),
              ),
            ),
            const SizedBox(width: 12.0),

            // --- Email Content ---
            Expanded(
              child: Padding(
                padding: const EdgeInsets.symmetric(vertical: 6.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start, // Align to right in RTL
                  children: [
                    // -- Top Row: Sender & Time --
                    Row(
                      mainAxisAlignment: MainAxisAlignment.spaceBetween,
                      children: [
                        Expanded(
                          child: Text(
                            email.sender,
                            style: theme.textTheme.titleMedium?.copyWith(
                              fontWeight: isUnread ? FontWeight.bold : FontWeight.normal,
                              fontSize: 15,
                            ),
                            maxLines: 1,
                            overflow: TextOverflow.ellipsis,
                            textAlign: TextAlign.start, // Align to right in RTL
                          ),
                        ),
                        SizedBox(width: 8),
                        Text(
                          _formatTimestamp(email.timestamp),
                          style: theme.textTheme.bodySmall?.copyWith(
                            color: isUnread ? theme.colorScheme.primary : Colors.grey.shade600,
                            fontWeight: isUnread ? FontWeight.bold : FontWeight.normal,
                            fontSize: 12,
                          ),
                        ),
                      ],
                    ),
                    const SizedBox(height: 2.0),

                    // -- Subject --
                    Text(
                      email.subject.isEmpty ? '(لا يوجد موضوع)' : email.subject, // نص عربي
                      maxLines: 1,
                      overflow: TextOverflow.ellipsis,
                      style: theme.textTheme.bodyMedium?.copyWith(
                         fontWeight: isUnread ? FontWeight.bold : FontWeight.normal,
                          color: theme.textTheme.bodyMedium?.color?.withOpacity(isUnread ? 1.0 : 0.8),
                          fontSize: 14,
                      ),
                      textAlign: TextAlign.start, // Align to right in RTL
                    ),
                    const SizedBox(height: 2.0),

                    // -- Preview & Star Icon Row --
                     Row(
                       mainAxisAlignment: MainAxisAlignment.spaceBetween,
                       crossAxisAlignment: CrossAxisAlignment.end,
                       children: [
                         Expanded(
                           child: Text(
                              email.preview,
                              maxLines: 1,
                              overflow: TextOverflow.ellipsis,
                              style: theme.textTheme.bodySmall?.copyWith(
                                  color: Colors.grey.shade600,
                                  fontSize: 13,
                              ),
                               textAlign: TextAlign.start, // Align to right in RTL
                            ),
                         ),
                          SizedBox(width: 4),
                          InkResponse(
                             onTap: () => onStarTap(email),
                             radius: 20,
                             child: Padding(
                               padding: const EdgeInsets.all(4.0),
                               child: Icon(
                                 email.isStarred ? Icons.star : Icons.star_border,
                                 color: email.isStarred ? Colors.amber.shade700 : Colors.grey.shade500,
                                 size: 20,
                               ),
                             ),
                           ),
                       ],
                     ),
                     // أيقونة المرفقات
                     if(email.hasAttachment)
                       Padding(
                         padding: const EdgeInsets.only(top: 4.0),
                         child: Icon(Icons.attachment_outlined, size: 16, color: Colors.grey.shade600),
                       ),
                  ],
                ),
              ),
            ),
             SizedBox(width: 8),
          ],
        ),
      ),
    );
  }

 // ودجت لبناء القائمة الجانبية (Drawer)
 Widget _buildDrawer(BuildContext context) {
   int unreadCount = emails.where((e) => e.isUnread).length;

  return Drawer(
    child: ListView(
      padding: EdgeInsets.zero,
      children: <Widget>[
        UserAccountsDrawerHeader(
          accountName: Text("اسم المستخدم"), // نص عربي
          accountEmail: Text("user@example.com"),
          currentAccountPicture: CircleAvatar(
            backgroundColor: Colors.blue,
            child: Text("U", style: TextStyle(fontSize: 40.0, color: Colors.white)),
          ),
          decoration: BoxDecoration(
            color: Theme.of(context).colorScheme.primary, // لون من الثيم
          ),
        ),
        ListTile(
          leading: Icon(Icons.inbox_outlined),
          title: Text('صندوق الوارد'), // نص عربي
           trailing: unreadCount > 0
              ? Chip(
                  label: Text(unreadCount.toString(), style: TextStyle(color: Colors.white, fontSize: 11)),
                  backgroundColor: Colors.red.shade700,
                  padding: EdgeInsets.symmetric(horizontal: 6, vertical: 0),
                  visualDensity: VisualDensity.compact,
                )
              : null,
          selected: true,
          onTap: () { Navigator.pop(context); },
        ),
         ListTile(
          leading: Icon(Icons.star_border_outlined),
          title: Text('المميزة بنجمة'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
        ListTile(
          leading: Icon(Icons.send_outlined),
          title: Text('المرسلة'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
         ListTile(
          leading: Icon(Icons.schedule_outlined),
          title: Text('المؤجلة'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
        ListTile(
          leading: Icon(Icons.drafts_outlined),
          title: Text('المسودات'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
         ListTile(
          leading: Icon(Icons.label_important_outline),
          title: Text('المهمة'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
        ListTile(
          leading: Icon(Icons.delete_outline),
          title: Text('المهملات'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Filter/Navigate */ },
        ),
        Divider(),
         ListTile(
          leading: Icon(Icons.settings_outlined),
          title: Text('الإعدادات'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Navigate to Settings */ },
        ),
         ListTile(
          leading: Icon(Icons.help_outline),
          title: Text('المساعدة والدعم'), // نص عربي
          onTap: () { Navigator.pop(context); /* TODO: Show Help */ },
        ),
      ],
    ),
  );
 }
}
```

---

الآن أصبح لديك مشروع Flutter منظم بالكامل مع جميع الملفات والكود المطلوب. بعد تطبيق هذه التغييرات، لا تنسَ تشغيل `flutter pub get` في مجلد مشروعك للتأكد من تحديث التبعيات.# kids
