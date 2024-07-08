حتماً، در ادامه فایل‌های پروژه به همراه توضیحات دقیق و جزئیات هر کدام ارائه شده است:

# پروژه دانشگاهی FastAPI

## مقدمه

این پروژه یک برنامه ساده FastAPI برای مدیریت داده‌های دانشگاه است. شامل قابلیت‌های مدیریت دانشجویان، دوره‌ها و اطلاعات ثبت‌نام می‌باشد. هدف اصلی، نمایش نحوه ساخت یک API RESTful با استفاده از FastAPI است.

## فهرست مطالب

- [نصب](#نصب)
- [استفاده](#استفاده)
- [ساختار پروژه](#ساختار-پروژه)
- [نقاط پایانی API](#نقاط-پایانی-api)
- [مشارکت](#مشارکت)
- [مجوز](#مجوز)

## نصب

1. مخزن را کلون کنید:
   ```bash
   git clone https://github.com/ThereWasLuna/fastapi-uni.git
   cd fastapi-uni
   ```

2. یک محیط مجازی ایجاد و فعال کنید:
   ```bash
   python -m venv env
   source env/bin/activate  # در ویندوز `env\Scripts\activate` استفاده کنید
   ```

3. وابستگی‌ها را نصب کنید:
   ```bash
   pip install -r requirements.txt
   ```

## استفاده

1. سرور را اجرا کنید:
   ```bash
   uvicorn main:app --reload
   ```

2. به آدرس زیر بروید:
   ```
   http://127.0.0.1:8000
   ```

## ساختار پروژه

```
fastapi-uni/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── models.py
│   ├── schemas.py
│   ├── crud.py
│   ├── database.py
│   ├── routers/
│   │   ├── __init__.py
│   │   ├── student.py
│   │   ├── course.py
│   │   ├── enrollment.py
│   └── tests/
│       ├── __init__.py
│       ├── test_main.py
│
├── requirements.txt
└── README.md
```

### توضیحات فایل‌ها

#### `main.py`
این فایل نقطه شروع برنامه است. شامل تنظیمات اصلی FastAPI، تعریف روترها و نقاط پایانی اصلی است. در اینجا برنامه FastAPI ایجاد و روترها به آن متصل می‌شوند.

#### `models.py`
این فایل شامل مدل‌های دیتابیس است که با استفاده از SQLAlchemy تعریف شده‌اند. این مدل‌ها ساختار جداول دیتابیس را تعیین می‌کنند. برای مثال، مدل‌های `Student`، `Course` و `Enrollment`.

#### `schemas.py`
این فایل شامل اسکیمای Pydantic برای اعتبارسنجی داده‌ها است. اسکیمای Pydantic برای تعریف ساختار و نوع داده‌های ورودی و خروجی استفاده می‌شود. برای مثال، `StudentCreate` و `StudentUpdate`.

#### `crud.py`
این فایل شامل عملیات CRUD (ایجاد، خواندن، بروزرسانی، حذف) برای تعامل با دیتابیس است. توابعی برای انجام عملیات‌های مختلف روی جداول دیتابیس، مانند ایجاد دانشجو، دریافت لیست دانشجویان و غیره در اینجا تعریف شده‌اند.

#### `database.py`
این فایل تنظیمات اتصال به دیتابیس را شامل می‌شود. اینجا می‌توان تنظیمات مربوط به موتور SQLAlchemy و ایجاد جلسه دیتابیس را یافت.

#### `routers/`
این پوشه شامل فایل‌های مربوط به روترهای API است که هر کدام به یکی از بخش‌های اصلی (دانشجویان، دوره‌ها و ثبت‌نام) اختصاص دارند.
- `student.py`: شامل نقاط پایانی مربوط به مدیریت دانشجویان، مانند ایجاد، خواندن، بروزرسانی و حذف دانشجو.
- `course.py`: شامل نقاط پایانی مربوط به مدیریت دوره‌ها، مانند ایجاد، خواندن، بروزرسانی و حذف دوره.
- `enrollment.py`: شامل نقاط پایانی مربوط به مدیریت ثبت‌نام‌ها، مانند ثبت‌نام یک دانشجو در یک دوره و حذف ثبت‌نام.

#### `tests/`
این پوشه شامل تست‌های واحد برای اپلیکیشن است.
- `test_main.py`: شامل تست‌هایی برای اطمینان از عملکرد صحیح نقاط پایانی و منطق برنامه.

#### `requirements.txt`
این فایل شامل لیست وابستگی‌های پروژه است که با استفاده از pip نصب می‌شوند. این وابستگی‌ها شامل بسته‌های مورد نیاز برای اجرای FastAPI، SQLAlchemy و دیگر کتابخانه‌ها است.

#### `README.md`
این فایل، راهنمای اصلی پروژه است که اطلاعات کلی درباره پروژه، نحوه نصب، استفاده و مشارکت در توسعه آن را ارائه می‌دهد.

## نقاط پایانی API

### دانشجویان

- `GET /students`: دریافت لیست دانشجویان.
- `POST /students`: ایجاد دانشجوی جدید.
- `GET /students/{student_id}`: دریافت اطلاعات یک دانشجو.
- `PUT /students/{student_id}`: بروزرسانی اطلاعات یک دانشجو.
- `DELETE /students/{student_id}`: حذف یک دانشجو.

### دوره‌ها

- `GET /courses`: دریافت لیست دوره‌ها.
- `POST /courses`: ایجاد دوره جدید.
- `GET /courses/{course_id}`: دریافت اطلاعات یک دوره.
- `PUT /courses/{course_id}`: بروزرسانی اطلاعات یک دوره.
- `DELETE /courses/{course_id}`: حذف یک دوره.

### ثبت‌نام

- `GET /enrollments`: دریافت لیست ثبت‌نام‌ها.
- `POST /enrollments`: ثبت‌نام یک دانشجو در یک دوره.
- `DELETE /enrollments/{enrollment_id}`: حذف ثبت‌نام.

## مشارکت

1. مخزن را فورک کنید.
2. یک شاخه جدید برای ویژگی یا باگ فیکس خود ایجاد کنید.
3. تغییرات خود را کامیت کنید.
4. شاخه خود را پوش کنید.
5. درخواست کشش (Pull Request) را ایجاد کنید.

## مجوز

این پروژه تحت مجوز MIT منتشر شده است. برای اطلاعات بیشتر فایل [LICENSE](LICENSE) را ببینید.
