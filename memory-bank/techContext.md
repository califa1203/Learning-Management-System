# Tech Context

## Technology Stack

### Core Framework
- **Next.js 15.3.3**: React framework with App Router
- **React 18.2.0**: UI library with modern hooks and patterns
- **TypeScript 5.2.2**: Static type checking and enhanced developer experience

### Styling & UI
- **Tailwind CSS 3.3.3**: Utility-first CSS framework
- **shadcn/UI**: Pre-built accessible component library
- **Radix UI**: Headless UI primitives for complex components
- **Lucide React**: Icon library for consistent iconography
- **tailwindcss-animate**: Animation utilities for Tailwind

### Development Tools
- **ESLint**: Code linting and style enforcement
- **PostCSS**: CSS processing and optimization
- **Autoprefixer**: Automatic vendor prefixing

### Form Handling & Validation
- **React Hook Form 7.57.0**: Performant form library
- **Zod 3.25.56**: TypeScript-first schema validation
- **@hookform/resolvers**: Integration between React Hook Form and Zod

### UI Enhancement Libraries
- **class-variance-authority**: Type-safe variant API for components
- **clsx**: Utility for constructing className strings
- **tailwind-merge**: Merge Tailwind classes without conflicts
- **cmdk**: Command palette component
- **sonner**: Toast notification system

### Data Visualization
- **Recharts 2.15.3**: Chart library for progress tracking and analytics

### Date Handling
- **date-fns 3.6.0**: Modern date utility library
- **react-day-picker 9.7.0**: Date picker component

### Layout & Interaction
- **react-resizable-panels 2.1.9**: Resizable panel layouts
- **embla-carousel-react 8.6.0**: Carousel component
- **vaul 0.9.9**: Drawer component for mobile interfaces

## Development Setup

### Project Structure
```
lms-project/
├── app/                    # Next.js App Router pages
│   ├── (dashboard)/       # Dashboard routes (grouped)
│   ├── auth/              # Authentication pages
│   ├── globals.css        # Global styles
│   └── layout.tsx         # Root layout
├── components/            # Reusable components
│   ├── ui/               # shadcn/UI components
│   ├── courses/          # Course-related components
│   ├── dashboard/        # Dashboard components
│   ├── home/             # Landing page components
│   └── navigation/       # Navigation components
├── lib/                  # Utility functions and services
├── types/                # TypeScript type definitions
├── hooks/                # Custom React hooks
├── memory-bank/          # Project documentation
└── public/               # Static assets
```

### Configuration Files
- **next.config.ts**: Next.js configuration
- **tailwind.config.ts**: Tailwind CSS configuration
- **tsconfig.json**: TypeScript configuration
- **eslint.config.mjs**: ESLint configuration
- **postcss.config.js**: PostCSS configuration
- **components.json**: shadcn/UI configuration

## Technical Constraints

### Current Limitations
- **No Database**: Using mock data with localStorage persistence
- **No Real Authentication**: Custom auth service for demo purposes
- **No Server State Management**: No global state management library
- **No Real-time Features**: No WebSocket or real-time capabilities yet
- **No File Upload**: No file handling or storage system
- **No Email System**: No email notifications or verification

### Browser Support
- Modern browsers supporting ES2020+
- Mobile-responsive design for iOS Safari and Chrome
- Progressive enhancement approach

### Performance Considerations
- Next.js automatic code splitting
- Image optimization ready (Next.js Image component available)
- CSS optimization through Tailwind's purging
- TypeScript compile-time optimizations

## Dependencies Analysis

### Production Dependencies (Key)
```json
{
  "next": "^15.3.3",
  "react": "18.2.0",
  "react-dom": "18.2.0",
  "typescript": "5.2.2",
  "tailwindcss": "3.3.3"
}
```

### UI Component Dependencies
- **@radix-ui/***: 20+ Radix UI primitives for accessible components
- **lucide-react**: Icon system
- **class-variance-authority**: Component variant management

### Form & Validation
- **react-hook-form**: Form state management
- **zod**: Schema validation
- **@hookform/resolvers**: Form validation integration

### Development Dependencies
- **@tailwindcss/postcss**: PostCSS integration
- **eslint**: Code quality
- **autoprefixer**: CSS vendor prefixing

## Tool Usage Patterns

### Component Development
1. **shadcn/UI First**: Use existing shadcn components when possible
2. **Custom Components**: Build custom components following shadcn patterns
3. **Tailwind Styling**: Utility-first approach with responsive design
4. **TypeScript Props**: Strongly typed component interfaces

### State Management
- **Local State**: React useState for component-level state
- **Form State**: React Hook Form for complex forms
- **Auth State**: Custom AuthService singleton
- **No Global State**: Currently no Redux/Zustand implementation

### Data Fetching Pattern (Prepared)
```typescript
// Ready for API integration
const fetchCourses = async () => {
  const response = await fetch('/api/courses');
  return response.json();
};
```

### Error Handling
- TypeScript compile-time error prevention
- Form validation with Zod schemas
- Try-catch blocks in async operations
- User-friendly error messages in UI

## Environment Setup Requirements

### Development Environment
- **Node.js**: Version 18+ required
- **Package Manager**: npm (package-lock.json present)
- **IDE**: VSCode recommended with extensions:
  - TypeScript and JavaScript Language Features
  - Tailwind CSS IntelliSense
  - ESLint
  - Prettier

### Required Environment Variables (Future)
```env
# Database
DATABASE_URL=postgresql://...

# Authentication (when implementing NextAuth)
NEXTAUTH_SECRET=...
NEXTAUTH_URL=...

# External Services (future)
PUSHER_APP_ID=...
PUSHER_KEY=...
PUSHER_SECRET=...
```

### Build & Deployment
- **Build Command**: `npm run build`
- **Dev Command**: `npm run dev`
- **Start Command**: `npm start`
- **Lint Command**: `npm run lint`

## Integration Points

### Ready for Database Integration
- TypeScript interfaces defined for all data models
- Mock data structure matches planned database schema
- API route structure prepared in Next.js

### Authentication Integration Points
- AuthService abstraction ready for NextAuth.js
- Role-based access control implemented
- Protected route patterns established

### Real-time Integration Points
- Component structure ready for WebSocket integration
- Message system architecture prepared
- Notification system foundation in place

## Performance Optimizations

### Current Optimizations
- Next.js automatic code splitting
- Tailwind CSS purging for smaller bundle size
- TypeScript for compile-time optimizations
- React 18 concurrent features ready

### Planned Optimizations
- Image optimization with Next.js Image component
- Database query optimization with proper indexing
- Caching strategies for frequently accessed data
- Lazy loading for heavy components

## Security Considerations

### Current Security Measures
- TypeScript for type safety
- Input validation with Zod schemas
- Role-based access control patterns
- Secure component patterns

### Planned Security Enhancements
- Proper session management with NextAuth.js
- CSRF protection for API routes
- Input sanitization for user-generated content
- Rate limiting for API endpoints
- Secure cookie configuration

## Migration Path

### From Mock Data to Database
1. Install Prisma ORM
2. Define database schema
3. Create migration files
4. Replace mock data imports with database queries
5. Implement proper error handling

### From Custom Auth to NextAuth.js
1. Install NextAuth.js and adapters
2. Configure providers and callbacks
3. Migrate existing auth patterns
4. Update middleware for session handling
5. Implement proper session management

### Adding Real-time Features
1. Choose WebSocket solution (Pusher, Socket.io, or native)
2. Implement real-time message system
3. Add live notifications
4. Implement presence indicators
5. Add typing indicators for chat
