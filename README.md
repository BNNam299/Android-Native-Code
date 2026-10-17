# Android Native Code

Bộ toolkit tiếng Việt giúp làm việc với AI coding agent để xây dựng ứng dụng di động: từ làm rõ yêu cầu, chọn kiến trúc, triển khai từng màn hình đến kiểm thử và chuẩn bị bản phát hành.

Trọng tâm của repo là **Android Native với Kotlin + Jetpack Compose**. Nội dung hiện có cũng bao gồm **React Native + Expo** và hướng dẫn chuyển đổi ứng dụng iOS sang Android hoặc React Native.

Repo chứa các tài liệu chỉ dẫn, skill, mẫu code trong Markdown và script PowerShell. Để tạo ra app chạy được, bạn cần dùng toolkit cùng một AI coding agent và môi trường phát triển phù hợp.

## Toolkit giúp bạn làm gì?

| Nhu cầu | Nội dung hỗ trợ | Kết quả hướng tới khi agent thực hiện |
|---|---|---|
| Bắt đầu một ứng dụng mới | Hỏi mục tiêu, tính năng, nền tảng và mức độ hiểu biết lập trình | Có phạm vi dự án và quy tắc làm việc rõ ràng |
| Xây dựng app Android | Kotlin, Compose, Material 3, ViewModel, StateFlow, Hilt | Code được tổ chức theo kiến trúc thống nhất |
| Làm nhiều màn hình | Mẫu UiState / Action / ViewModel, điều hướng và quản lý state | Thêm tính năng theo từng bước, dễ đối chiếu |
| Kết nối API và lưu dữ liệu | Mẫu Repository, Retrofit, Room, DataStore, phân tách model | Có hướng dẫn xây dựng tầng dữ liệu và xử lý lỗi |
| Làm camera hoặc nhận diện tư thế | Tài liệu CameraX, MediaPipe và xử lý hệ tọa độ | Có cơ sở triển khai tính năng phụ thuộc thiết bị |
| Chuyển app iOS sang Android | Phân loại thuật toán, cầu nối nền tảng và giao diện | Có kế hoạch chuyển đổi và kiểm chứng kết quả từng tầng |
| Kiểm tra chất lượng | Skill review, mẫu test ViewModel/Compose, hướng dẫn lint và kiểm tra trên thiết bị | Phát hiện lỗi trước khi bàn giao |
| Tạo bản demo và chuẩn bị phát hành | Quy trình build, cài trên thiết bị, tạo APK và hướng dẫn release | Có bản để thử nghiệm và các bước chuẩn bị phát hành |
| Làm app đa nền tảng | Nhánh React Native + Expo với skill và quy trình riêng | Có hướng triển khai chung cho Android và iOS |

Các kết quả trên phụ thuộc vào việc agent đọc và thực hiện hướng dẫn, yêu cầu đầu vào, công cụ sẵn có và quá trình kiểm thử thực tế.

## Cách toolkit hoạt động

Điểm bắt đầu là [BOOTSTRAP.md](BOOTSTRAP.md). Agent được hướng dẫn làm rõ dự án mới hay chuyển đổi code cũ, chọn nền tảng, chọn cách giao tiếp phù hợp với người dùng và thu thập thông tin sản phẩm.

Sau đó, agent kết hợp các lớp tài liệu:

1. **Nguyên tắc chung:** giới hạn phạm vi, giữ code đơn giản, kiểm chứng nguồn tham khảo và ghi lại lỗi đặc thù của dự án.
2. **Hồ sơ người dùng:** điều chỉnh cách giải thích cho người có hoặc chưa có kinh nghiệm lập trình.
3. **Quy định theo nền tảng:** kiến trúc, thư viện và cách tổ chức code.
4. **Skill và mẫu tham khảo:** nạp nội dung phù hợp với công việc đang làm.
5. **Quy trình triển khai:** khởi tạo → khung điều hướng → từng tính năng → hoàn thiện → demo hoặc phát hành.

BOOTSTRAP hướng dẫn tạo `CLAUDE.md`, `AGENTS.md` và `FOOTGUNS.md` tại gốc dự án. Các giai đoạn có điểm dừng để người dùng xem kết quả và duyệt bước tiếp theo.

## Khả năng Android Native

Nhánh Android có **12 skill chuyên biệt**, cộng **2 skill dùng chung** cho review code và Postgres/Supabase. Các skill được lưu sẵn trong repo; nhánh này không yêu cầu chạy script cài plugin Expo.

| Nhóm | Phạm vi |
|---|---|
| Jetpack Compose | State, side effect, thiết kế component, animation, focus, hiệu năng và UI test |
| Kotlin | Coroutine/Flow, thiết kế API và control flow |
| Build và trải nghiệm app | Chạy Gradle, hướng dẫn xử lý lỗi, accessibility, màn hình thích ứng, bảo mật và Material 3 |
| Mẫu kiến trúc | MVI trên luồng dữ liệu một chiều, UI/Data layer và Domain layer khi cần |
| Mẫu dữ liệu | Tách DTO / Entity / Domain model, Repository và xử lý offline |

Các mẫu nằm trong [reusable-modules/android-native/](reusable-modules/android-native/). Đây là tài liệu và đoạn code tham khảo để áp dụng vào dự án, cần điều chỉnh và kiểm tra trong môi trường thực tế.

Quy định công nghệ của toolkit nằm tại [tech-stacks/android-native.md](tech-stacks/android-native.md), bao gồm lựa chọn Navigation Compose 2 với route có kiểu dữ liệu. Đây là lựa chọn của bản toolkit hiện tại; khi triển khai cần đối chiếu phiên bản và tài liệu liên quan.

## Chuyển đổi code iOS

Hướng dẫn [iOS Native → Android Native](migration/ios-native-to-android-native.md) chia code cũ thành ba nhóm:

- **Thuật toán thuần:** chuyển logic tính toán sang Kotlin và viết test đối chiếu đầu vào/đầu ra.
- **Cầu nối nền tảng:** viết lại camera, cảm biến, ML và lưu trữ bằng API Android; kiểm chứng đơn vị, hệ tọa độ và kết quả.
- **Giao diện:** dựng lại bằng Compose sau khi các tầng logic đã được kiểm tra.

Cách chia này giúp tập trung vào phần khó của quá trình chuyển đổi: bảo toàn hành vi sản phẩm. Với camera và nhận diện tư thế, đổi framework hoặc model có thể làm thay đổi kết quả; cần dữ liệu mẫu và kiểm tra trên thiết bị.

Repo cũng có [hướng dẫn iOS → React Native](migration/ios-native-to-rn.md). Phần Android → React Native hiện mới là placeholder.

## Bắt đầu sử dụng

### 1. Tải toolkit

Nếu chỉ muốn đọc hoặc lưu repo:

```powershell
git clone https://github.com/BNNam299/Android-Native-Code.git
```

Lệnh này tạo thư mục `Android-Native-Code` chứa toàn bộ toolkit.

Để dùng trong một dự án mới theo đúng đường dẫn trong các tài liệu hiện có, chạy từ **gốc dự án của bạn**:

```powershell
git clone https://github.com/BNNam299/Android-Native-Code.git toolkit/03-dev-code
```

Cấu trúc khi đó:

```text
my-app/
└── toolkit/
    └── 03-dev-code/
        ├── BOOTSTRAP.md
        ├── attach-skills.ps1
        ├── SKILL/
        └── ...
```

### 2. Mở dự án bằng AI coding agent

Bạn có thể đưa yêu cầu bắt đầu như sau:

```text
Đọc toolkit/03-dev-code/BOOTSTRAP.md và hướng dẫn tôi khởi tạo dự án.
Tôi muốn làm app Android Native bằng Kotlin + Jetpack Compose.
Tôi chưa chuyên về lập trình.
Mục tiêu ứng dụng: [mô tả].
Hãy làm rõ yêu cầu và thực hiện theo các giai đoạn của toolkit.
```

Nếu chuyển đổi app iOS, bổ sung rằng bạn đã có code Swift và muốn chuyển sang Android Native. Agent sẽ theo nhánh migration tương ứng.

### 3. Gắn skill theo nền tảng

BOOTSTRAP có bước hướng dẫn chạy lệnh này từ **gốc dự án**:

```powershell
.\toolkit\03-dev-code\attach-skills.ps1 -Stack android-native
```

Script copy skill dùng chung và skill Android vào `.claude/skills/` của dự án. Script hiện chỉ ghi vào đường dẫn này; nếu agent của bạn dùng vị trí skill khác, cần cấu hình tương ứng hoặc yêu cầu agent đọc trực tiếp các file trong toolkit.

Với React Native + Expo, tham khảo [SETUP.md](SETUP.md) và dùng `-Stack react-native-expo`. Script `setup-machine.ps1` dành cho luồng plugin của Claude Code; cần đọc trước khi chạy trong môi trường khác.

Để phát triển Android, bạn vẫn cần Android Studio, SDK/JDK phù hợp và thiết bị thật hoặc máy ảo. Toolkit không tự cài toàn bộ môi trường phát triển. Việc dùng AI agent và dịch vụ bên ngoài có thể phát sinh chi phí riêng.

## Cấu trúc repo

| Đường dẫn | Vai trò |
|---|---|
| [BOOTSTRAP.md](BOOTSTRAP.md) | Điểm bắt đầu và điều phối khởi tạo dự án |
| [project-template.md](project-template.md) | Mẫu thông tin sản phẩm, tính năng và ràng buộc |
| [global/](global/) | Nguyên tắc code, sử dụng context và ghi nhận lỗi |
| [user-profiles/](user-profiles/) | Cách làm việc với người dùng chuyên/không chuyên |
| [tech-stacks/](tech-stacks/) | Quy định công nghệ theo nền tảng |
| [SKILL/](SKILL/) | Skill Android, React Native và skill dùng chung |
| [reusable-modules/](reusable-modules/) | Mẫu kiến trúc, dữ liệu, điều hướng, camera và test |
| [build-sequences/](build-sequences/) | Trình tự triển khai theo giai đoạn |
| [migration/](migration/) | Quy trình chuyển đổi code giữa các nền tảng |
| [addons/backend-supabase.md](addons/backend-supabase.md) | Hướng dẫn bổ sung backend Supabase khi cần |
| [attach-skills.ps1](attach-skills.ps1) | Copy skill vào dự án theo stack |
| [SETUP.md](SETUP.md) | Hướng dẫn phụ thuộc và plugin cho luồng liên quan |

## Đánh giá và giới hạn hiện tại

**Điểm mạnh:** toolkit kết hợp quy trình, quy định kiến trúc và tài liệu chuyên môn trong cùng một repo. Người dùng có một điểm bắt đầu rõ ràng, còn agent có mẫu để làm việc nhất quán. Việc tách skill theo stack và ghi lỗi vào `FOOTGUNS.md` giúp quản lý kiến thức theo từng dự án.

**Phù hợp với:** cá nhân hoặc nhóm nhỏ dùng AI để xây dựng app Android, người chưa chuyên lập trình cần hướng dẫn từng bước, và dự án cần phân tích code iOS trước khi chuyển nền tảng. Nhánh React Native + Expo phục vụ nhu cầu phát triển đa nền tảng.

**Những phần cần biết trước khi dùng:**

- Theo ghi chú tổng quan của toolkit gốc, quy trình chưa được chạy thử trọn vẹn trên một dự án thực tế; cần kiểm chứng từ đầu đến cuối trước khi xem là quy trình đã ổn định.
- `project-template.md` còn là bản nháp; iOS Native và Android → React Native chưa được triển khai đầy đủ.
- Tài liệu có một số chỗ cần đồng bộ, chẳng hạn `SETUP.md` còn ghi 11 skill Android trong khi thư mục hiện có 12. Phiên bản, chính sách phát hành và thông tin dịch vụ cần kiểm tra lại khi sử dụng.
- Skill lưu trong repo là bản sao tại thời điểm đưa vào, không tự cập nhật theo nguồn gốc. Một số hướng dẫn plugin và đường dẫn skill hiện thiên về Claude Code.
- Repo này tập trung vào giai đoạn phát triển. Những giai đoạn nghiên cứu sản phẩm, PRD, thiết kế UI và QA độc lập của toolkit gốc không nằm trong repo này.
- Chất lượng app vẫn cần được xác nhận bằng build, test, review và thử trên thiết bị. Mức tiết kiệm thời gian, token hoặc mức độ tương đương sau migration chưa có số liệu đo trong repo.

## Nguồn skill

Các nhóm skill được đưa vào từ những nguồn được ghi trong tài liệu của toolkit, gồm `chrisbanes/skills`, `MiniMax-AI/skills`, Callstack và Vercel. Xem từng thư mục trong [SKILL/](SKILL/) để biết nội dung và nguồn tương ứng. Khi sử dụng lại hoặc phân phối, kiểm tra điều khoản và giấy phép của từng nguồn.
