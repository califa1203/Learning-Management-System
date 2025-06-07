# System Patterns

## System Architecture

### Frontend Architecture
- **Framework**: Next.js 15+ with App Router for modern React development
- **Component Architecture**: Component-driven development with reusable UI components
- **Styling**: Tailwind CSS utility-first approach with shadcn/UI component library
- **State Management**: React hooks and local state (no global state management yet)
- **Type Safety**: TypeScript throughout for robust type checking

### Backend Architecture (Current)
- **Data Layer**: Mock data service with localStorage persistence
- **Authentication**: Custom AuthService class with role-based access control
- **API Pattern**: Next.js API routes (prepared for database integration)

### Planned Database Architecture
- **Database**: PostgreSQL with Vercel integration
- **ORM**: Prisma (recommended for type-safe database access)
- **Tables**: Users, Courses, Lessons, Quizzes, Questions, Progress, Messages, Notifications

## Key Technical Decisions

### 1. Next.js App Router
**Decision**: Use Next.js 13+ App Router instead of Pages Router
**Rationale**: 
- Modern React patterns with Server Components
- Better file-based routing organization
- Improved performance with streaming and suspense
- Future-proof architecture

### 2. Component Library Strategy
**Decision**: shadcn/UI + Tailwind CSS combination
**Rationale**:
- Pre-built accessible components
- Customizable and maintainable
- Consistent design system
- Rapid development without sacrificing quality

### 3. Authentication Pattern
**Decision**: Custom AuthService with role-based access control
**Rationale**:
- Full control over authentication flow
- Easy integration with multiple user roles
- Prepared for NextAuth.js migration
- Simple demo implementation for development

### 4. File Organization
**Decision**: Feature-based organization with clear separation
**Rationale**:
- Scalable structure as features grow
- Clear separation of concerns
- Easy to locate and maintain code
- Follows Next.js best practices

## Design Patterns in Use

### 1. Component Composition Pattern
```typescript
// Example: Course components
<CourseGrid>
  <CourseCard />
  <CourseCard />
</CourseGrid>
```
- Reusable components that compose together
- Props-based customization
- Single responsibility principle

### 2. Service Layer Pattern
```typescript
// AuthService singleton pattern
export const authService = AuthService.getInstance();
```
- Centralized business logic
- Consistent API across components
- Easy to test and mock

### 3. Type-First Development
```typescript
// Comprehensive type definitions
interface User {
  id: string;
  role: 'student' | 'teacher' | 'parent' | 'admin';
  // ...
}
```
- All data structures defined as TypeScript interfaces
- Compile-time error catching
- Better IDE support and autocomplete

### 4. Role-Based Access Control (RBAC)
```typescript
// Route protection based on user roles
const user = authService.getCurrentUser();
if (user?.role !== 'admin') {
  // Redirect or show error
}
```
- Centralized permission checking
- Consistent across all components
- Easy to extend with new roles

## Component Relationships

### Core Component Hierarchy
```
App Layout (layout.tsx)
├── Navbar (global navigation)
├── Page Components
│   ├── Landing Page (/)
│   │   ├── HeroSection
│   │   ├── FullCourseGrid
│   │   └── CourseGrid
│   ├── Auth Pages (/auth/*)
│   │   ├── LoginPage
│   │   └── RegisterPage
│   └── Dashboard Pages (/dashboard/*)
│       ├── AdminDashboard
│       ├── TeacherDashboard
│       ├── StudentDashboard
│       └── ParentDashboard
└── UI Components (/components/ui/*)
    ├── Button, Card, Input, etc.
    └── Custom components
```

### Data Flow Patterns
1. **Mock Data → Components**: Currently using imported mock data
2. **Auth State → Components**: AuthService provides user context
3. **Form Data → API**: Form submissions prepared for API integration
4. **Component State → UI**: Local state management with React hooks

## Critical Implementation Paths

### 1. Authentication Flow
```
Login Form → AuthService.login() → User Object → Role-based Redirect → Dashboard
```

### 2. Course Display Flow
```
Page Load → Mock Data Import → CourseGrid Component → CourseCard Rendering
```

### 3. Navigation Flow
```
User Role Check → Conditional Menu Items → Role-based Route Access
```

### 4. Dashboard Access Flow
```
Route Access → Auth Check → Role Verification → Dashboard Component Render
```

## Established Conventions

### File Naming
- Components: PascalCase (e.g., `HeroSection.tsx`)
- Pages: kebab-case (e.g., `login/page.tsx`)
- Utilities: camelCase (e.g., `auth.ts`)
- Types: PascalCase interfaces (e.g., `User`, `Course`)

### Component Structure
```typescript
// Standard component pattern
interface ComponentProps {
  // Props definition
}

export function ComponentName({ prop1, prop2 }: ComponentProps) {
  // Component logic
  return (
    // JSX with Tailwind classes
  );
}
```

### Import Organization
1. React/Next.js imports
2. Third-party library imports
3. Internal component imports
4. Type imports
5. Utility imports

### CSS/Styling Patterns
- Tailwind utility classes for styling
- Responsive design with Tailwind breakpoints
- shadcn/UI components for complex interactions
- Consistent spacing and color schemes

## Future Architecture Considerations

### Database Integration
- Replace mock data with Prisma ORM
- Implement proper API routes with database queries
- Add data validation with Zod schemas

### Real-time Features
- WebSocket integration for live chat
- Real-time notifications
- Live progress updates

### Performance Optimization
- Image optimization with Next.js Image component
- Code splitting for large components
- Caching strategies for frequently accessed data

### Security Enhancements
- Proper session management
- CSRF protection
- Input sanitization and validation
- Rate limiting for API routes
