# Practice Platform - System Specification v1.1

## 1. Introduction & Purpose
A modern practice platform designed for interview preparation and skill building across technologies.  
It enables progress tracking, personalized feedback, and continuous learning.

## 2. Tech Stack
- **Backend**: Laravel 12 (PHP 8.2+)
- **Database**: MySQL 8.0+
- **Frontend**: Blade/Inertia + React 18 + TailwindCSS
- **Authentication**: Laravel Socialite, Sanctum, optional Fortify
- **Deployment**: GitHub repo, Docker-ready

## 3. Core Features (Base Release)
- User registration/login via SSO (Google, Microsoft, GitHub)  
- Progress tracking & dashboard  
- Personalized recommendations  
- Notifications & alerts  
- Role-based access control  
- Organization mapping (via email domain)  
- Modern UI/UX (responsive)

## 4. SSO Design
**Protocols**: OIDC/OAuth2 (Google/Microsoft/GitHub), SAML 2.0 (future)  
**Packages**: Socialite + Sanctum, laravel-saml2  
**Flow**: Redirect → IdP → Callback → Map attributes → User creation/login  
**Attributes**: email, name, avatar, org_id, roles  
**Security**: state/nonce validation, signed assertions, HTTPS-only cookies, 2FA (optional)  
**Admin Settings**: allowed providers, default roles, org mapping  

## 5. Database Schema (Minimal)
- **users**(id, name, email, email_verified_at, password, avatar_url, org_id, …)  
- **user_providers**(id, user_id, provider, provider_user_id)  
- **roles & permissions** (via spatie/laravel-permission)  
- **organizations**(id, name, slug, email_domain, settings)  

## 6. Release Plan
- **Sprint 1 (Base)**: OIDC SSO (Google, Microsoft, GitHub), progress tracking, notifications, roles  
- **Sprint 2**: SAML, 2FA enforcement, audit logs, SCIM-lite import  
- **Sprint 3**: Advanced role rules, IdP metadata UI, profile enrichment  

## 7. Non-functional Requirements
- **Security**: Encrypted storage, secure sessions  
- **Performance**: Scalable to 10k concurrent users  
- **Availability**: 99.9% uptime target  
- **Extensibility**: Modular service-oriented architecture  
- **Compliance**: GDPR-ready, audit logs for enterprise
