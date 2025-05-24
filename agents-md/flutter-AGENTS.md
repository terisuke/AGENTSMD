# AGENTS.md - Flutter Project Contributor Guide

Welcome to this Flutter project repository. This file contains the main points for new contributors and AI assistants working with Flutter/Dart projects.

## Repository overview
- **Source code**: `lib/` contains the main application code organized by features.
- **Core**: `lib/core/` for constants, errors, utilities, and themes.
- **Data layer**: `lib/data/` for models, repositories, and external services.
- **Domain layer**: `lib/domain/` for entities, use cases, and business logic.
- **Presentation**: `lib/presentation/` for UI components, pages, and state management.
- **Tests**: `test/` with unit, widget, and integration test directories.
- **Assets**: `assets/` for images, icons, fonts, and other static resources.

## Local workflow
1. Set up Flutter environment and dependencies:
   ```bash
   flutter doctor             # Check Flutter installation
   flutter pub get            # Get dependencies
   flutter pub run build_runner build # Generate code (if using code generation)
   ```

2. Format, analyze and check your changes:
   ```bash
   dart format .              # Format Dart code
   dart analyze               # Static analysis
   flutter test               # Run all tests
   ```

3. Run the application:
   ```bash
   flutter run                # Run on connected device/emulator
   flutter run -d chrome      # Run web version
   flutter run --release      # Run in release mode
   ```

4. Build for production:
   ```bash
   flutter build apk          # Android APK
   flutter build ios          # iOS build
   flutter build web          # Web build
   flutter build windows      # Windows build (if configured)
   ```

## Testing guidelines
Use Flutter's built-in testing framework with comprehensive coverage:
```bash
flutter test --coverage      # Generate coverage report
flutter test test/unit/       # Run unit tests only
flutter test test/widget/     # Run widget tests only
flutter test integration_test/ # Run integration tests
```
- Test all public methods and critical user flows
- Use widget tests for UI component verification
- Implement golden tests for visual regression testing
- Test state management (Riverpod providers)
- Include integration tests for complete user scenarios

## Style notes
- Follow Effective Dart guidelines for code style.
- Use `const` constructors wherever possible for performance.
- Prefer Stateless widgets over Stateful when state is not needed.
- Use meaningful names following Dart naming conventions.
- Implement proper error handling with try-catch blocks.
- Use `async`/`await` for asynchronous operations.

## Commit message format
Use conventional commit format:
```
type(scope): description

Examples:
feat(auth): implement biometric authentication
fix(ui): resolve overflow issue on small screens
perf(list): optimize ListView performance with builder
refactor(state): migrate to Riverpod 2.0 providers
test(models): add comprehensive user model tests
style(widgets): update theme consistency across app
```

## Pull request expectations
PRs should include:
- **Summary**: Clear description of functionality and user experience changes
- **Screenshots**: Visual proof on multiple platforms (iOS/Android/Web)
- **Performance impact**: Frame rate and memory usage considerations
- **Platform compatibility**: Testing across target platforms
- **Accessibility**: Screen reader and navigation accessibility verification

Before submitting, ensure:
- [ ] All tests pass (`flutter test`)
- [ ] No analyzer warnings (`dart analyze`)
- [ ] Code is formatted (`dart format .`)
- [ ] App builds successfully on target platforms
- [ ] UI is responsive across different screen sizes
- [ ] Accessibility features work properly
- [ ] Performance is acceptable (60fps target)

## What reviewers look for
- **Widget architecture**: Proper widget composition and separation of concerns.
- **State management**: Effective use of Riverpod providers and state handling.
- **Performance**: Efficient rendering and memory management.
- **Platform compliance**: Following Material Design and Cupertino guidelines.
- **Accessibility**: Proper Semantics widget usage and navigation support.
- **Code quality**: Null safety compliance and error handling.

## Flutter architecture guidelines
- Follow Clean Architecture principles with clear layer separation.
- Use Feature-First directory structure for scalability.
- Implement Repository pattern for data access abstraction.
- Apply MVVM pattern with proper separation of concerns.
- Use dependency injection for better testability.

## Widget best practices
- Prefer composition over inheritance for widget design.
- Use `const` constructors to improve performance.
- Implement proper `Key` usage for widget identity.
- Create reusable widgets with clear, focused responsibilities.
- Use `Builder` widgets to manage context scope appropriately.
- Implement proper disposal of resources in `dispose()` methods.

## Riverpod state management
- Design providers with appropriate granularity.
- Use `StateProvider` for simple state, `StateNotifierProvider` for complex state.
- Apply `autodispose` modifier to prevent memory leaks.
- Use `family` modifier for parameterized providers.
- Implement proper error handling in providers.
- Test providers in isolation with appropriate mocking.

## Performance optimization
- Use `ListView.builder` for large lists instead of `ListView`.
- Implement `RepaintBoundary` for expensive widgets.
- Apply `AutomaticKeepAliveClientMixin` for preserving state.
- Use `ValueListenableBuilder` for granular rebuilds.
- Implement image caching and optimization strategies.
- Monitor performance with Flutter Inspector and DevTools.

## Platform-specific considerations
- Follow Material Design guidelines for Android.
- Implement Cupertino design patterns for iOS.
- Use `Platform.isIOS` and `Platform.isAndroid` for platform-specific code.
- Implement proper platform channels for native functionality.
- Test on real devices, not just simulators/emulators.
- Handle platform-specific permissions appropriately.

## Data management
- Use `json_annotation` with `json_serializable` for JSON serialization.
- Implement proper local storage with Hive or shared_preferences.
- Use HTTP clients with proper error handling and timeouts.
- Apply caching strategies for improved performance.
- Handle offline scenarios gracefully.
- Implement proper data validation and sanitization.

## UI/UX guidelines
- Follow platform design guidelines (Material/Cupertino).
- Implement responsive design for different screen sizes.
- Support both light and dark themes.
- Use proper spacing and typography from design system.
- Implement smooth animations and transitions.
- Provide proper loading states and error handling.

## Accessibility best practices
- Use `Semantics` widget for screen reader support.
- Implement proper focus management and navigation.
- Ensure sufficient color contrast ratios.
- Provide alternative text for images and icons.
- Test with TalkBack (Android) and VoiceOver (iOS).
- Support dynamic font sizing and high contrast modes.

## Security considerations
- Validate all user inputs and API responses.
- Use secure storage for sensitive data (flutter_secure_storage).
- Implement proper authentication and session management.
- Protect against common vulnerabilities (XSS, injection attacks).
- Use HTTPS for all network communications.
- Implement proper certificate pinning for production apps.

## Testing strategies
- Write unit tests for business logic and utility functions.
- Create widget tests for UI components and user interactions.
- Implement integration tests for complete user flows.
- Use golden tests for visual regression testing.
- Mock external dependencies appropriately.
- Test error scenarios and edge cases thoroughly.
