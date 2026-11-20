# my-humanoid-journey

> *"Điều tôi nghe, tôi quên. Điều tôi thấy, tôi nhớ. Điều tôi làm, tôi hiểu."* — **Khổng Tử**

Repository lưu trữ mã nguồn, mô phỏng và quá trình tự học **Humanoid Robotics & AI** từ con số 0: **11 module (`M0` - `M10`)**, **~130 giờ**, ngân sách mục tiêu **1.000.000 VNĐ**.

- **Phạm vi minh bạch:** Phần cứng thực tế là **Otto DIY** (robot 2 chân, 4 DoF); phần **Humanoid 12 DoF** (học đi bằng RL & mô phỏng thao tác) được thực hiện trong **NVIDIA Isaac Sim / Isaac Lab**.
- **Đích đến:** Chứng minh trọn vẹn pipeline **Sim-to-Real** (`PPO -> ONNX -> Otto thật qua ROS 2`) cùng bộ portfolio sẵn sàng ứng tuyển lab robotics / thực tập.

## 1. Chiến lược cốt lõi: *"Mô phỏng là chính, phần cứng là proxy"*

| Trụ cột | Công cụ / Nền tảng | Vai trò |
| :--- | :--- | :--- |
| **Mô phỏng (Miễn phí)** | NVIDIA Isaac Sim, Isaac Lab, Google Colab (GPU T4) | Môi trường huấn luyện RL (PPO) & Computer Vision (YOLOv8n) cho humanoid ảo 12 DoF. |
| **Phần cứng proxy** | Otto DIY (Arduino Nano, 4 servo SG90, HC-SR04, MPU6050) | Robot 2 chân 4 DoF cùng nguyên lý thăng bằng động với humanoid nhưng đơn giản hơn 10 lần. |
| **Cầu nối Sim-to-Real** | ROS 2 Humble, `ros2_control`, ONNX | Đưa policy từ Isaac Lab chạy trên Otto thật qua serial (mục tiêu độ trễ dưới 50 ms). |

## 2. Cấu trúc Repository

~~~text
my-humanoid-journey/
├── ai/              # Huấn luyện RL (Isaac Lab / PPO), export ONNX, YOLOv8n
├── docs/            # Ghi chú nền tảng (00-notes.md) & nhật ký học tập (journal.md)
├── firmware/        # Code Arduino Nano / PlatformIO (servo, cảm biến, Otto DIY)
├── guide_files/     # Tài liệu hướng dẫn chi tiết về kỹ thuật làm việc
├── hardware/        # File 3D (STL), sơ đồ mạch, hướng dẫn lắp ráp
├── road_map/        # Tài liệu lộ trình tự học tổng quan
├── ros2/            # ROS 2 Humble packages (serial_bridge, URDF/xacro, ros2_control, CV node)
├── sim/             # Kịch bản mô phỏng NVIDIA Isaac Sim (USD, Articulation API)
└── README.md
~~~

## 3. Lộ trình 11 Module (~130 giờ)

*Nguyên tắc: Mỗi checkpoint là điều kiện bắt buộc để sang module tiếp theo. Học theo quy tắc **30% lý thuyết - 30% drill - 40% tự làm**.*

| Module | Nội dung chính | Tuần | Giờ | Đầu ra / Checkpoint bắt buộc | Trạng thái |
| :--- | :--- | :---: | :---: | :--- | :---: |
| **M0** | Nền tảng & Setup môi trường | 1 | 4 | Repo đúng cấu trúc + `docs/00-notes.md` (3/3 câu hỏi) + Tinkercad LED | Chưa làm |
| **M1** | Điện tử căn bản + Arduino Nano | 2-6 | 20 | Video servo quét mượt + đọc ổn định HC-SR04 & IMU (MPU6050) | Chưa làm |
| **M2** | Otto DIY (robot 2 chân 4 DoF) | 7-10 | 15 | Video Otto đi bộ + né vật cản + điều khiển Bluetooth | Chưa làm |
| **M3** | ROS 2 cơ bản (Humble) | 11-13 | 15 | Otto thật nhận lệnh `/joint_commands` từ node ROS 2 qua serial | Chưa làm |
| **M4** | URDF + TF2 + RViz2 | 14-16 | 15 | `mini_humanoid.urdf` (12 DoF) trong RViz2 + test `ros2_control` | Chưa làm |
| **M5** | NVIDIA Isaac Sim | 17-18 | 12 | `mini_humanoid` chạy trong Isaac Sim, điều khiển 12 joint bằng Python | Chưa làm |
| **M6** | Reinforcement Learning (Isaac Lab) | 19-21 | 18 | Policy PPO (`.pt`), humanoid ảo đi ổn định tối thiểu 5 bước + Domain Randomization | Chưa làm |
| **M7** | Sim-to-Real trên Otto | 22-23 | 10 | Policy ONNX chạy trên Otto thật + báo cáo độ trễ (dưới 50 ms) & sim-vs-real | Chưa làm |
| **M8** | Cánh tay & Manipulation | 24-25 | 10 | Video cánh tay (ảo hoặc thật) gắp/đặt vật + code giải thích IK | Chưa làm |
| **M9** | Perception (YOLOv8n + IMU fusion) | 26 | 6 | Video robot nhận diện vật + phản ứng + báo cáo FPS & độ chính xác | Chưa làm |
| **M10** | Tổng kết & Portfolio | 27 | 5 | Repo public + Blog kỹ thuật (~1500 từ) + Video demo 3 phút | Chưa làm |

## 4. Thiết lập môi trường & Ngân sách

### Môi trường phát triển (100% miễn phí)

- **Hệ thống:** Ubuntu 22.04 LTS (native hoặc WSL2 trên Windows), Python `3.11+`, Git & GitHub.
- **IDE & Mô phỏng mạch:** VS Code (extensions: `Python`, `C/C++`, `ROS`, `PlatformIO IDE`), Arduino IDE / PlatformIO, [Tinkercad Circuits](https://www.tinkercad.com).
- **Tài khoản bắt buộc:** [NVIDIA Developer](https://developer.nvidia.com) (tải & kích hoạt Isaac Sim) và [Google Colab](https://colab.research.google.com) (GPU NVIDIA T4, 16 GB VRAM).

### Tóm tắt ngân sách phần cứng

| Tầng | Phạm vi | Thành phần chính | Chi phí |
| :--- | :--- | :--- | :--- |
| **Tầng 1 (Bắt buộc)** | Hoàn thành `M0` - `M7` | Arduino Nano + shield, 4 servo SG90, in 3D khung Otto, nguồn 4 pin AA + LM2596, HC-SR04, MPU6050, phụ kiện & dự phòng | **825.000 VNĐ** *(dư ~175k trong mức 1 triệu)* |
| **Tầng 2 (Tùy chọn)** | Phần cứng `M8` *(sau M7)* | 3 servo MG996R, 1 servo SG90 (gripper), in 3D cánh tay, khớp nối + ốc, pin LiPo 2S + mạch sạc | **700.000 VNĐ** *(có thể làm M8 trong sim)* |

> **Lưu ý:** Không mua Raspberry Pi ở giai đoạn này; laptop + cáp USB đáp ứng đủ toàn bộ lộ trình.

## 5. Tiêu chí hoàn thành ("Sẵn sàng thực tập Robotics")

- [ ] Otto thật đi được từ lệnh **ROS 2** (không phụ thuộc Arduino IDE).
- [ ] Giải thích rõ bản chất: nguồn riêng cho servo, calibrate servo và khái niệm DoF.
- [ ] Policy **PPO** (`Isaac Lab -> ONNX`) chạy trên Otto thật kèm số liệu độ trễ và phân tích sim-to-real.
- [ ] Repo public sạch sẽ, có hướng dẫn tái tạo (reproducible) cho người đọc.
- [ ] Có **video demo 3 phút** + **blog kỹ thuật** kể rõ hành trình: `Otto 4 DoF -> Humanoid 12 DoF trong sim -> Sim-to-Real`.
- [ ] Trình bày trung thực giới hạn dự án (phần cứng là Otto, phần humanoid làm trong mô phỏng).

## 6. Nguồn gốc & Tài nguyên tham khảo

**Tài liệu gốc xây dựng lộ trình:**
1. `lo_trinh_humanoid_robotics_ai.pdf` — *Lộ trình Tự học: Humanoid Robotics & Artificial Intelligence (11 module, ~130 giờ)*.
2. `Module_0_Humanoid_Robotics.pdf` — *Module 0: Nền tảng & Setup môi trường*.

**Tài nguyên kỹ thuật chính (trích từ tài liệu gốc):**
- **Tổng quan & Phần cứng:** *"HUMANOID ROBOTS"* (*Science Robotics*, 2026); *"Teardown of a Humanoid Robot"* (*EET China*, 2026); [github.com/OttoDIY](https://github.com/OttoDIY) & [ottodiy.com](https://ottodiy.com); [Tinkercad Circuits](https://www.tinkercad.com) & [arduino.cc/reference](https://www.arduino.cc/reference).
- **ROS 2 & Mô phỏng:** [docs.ros.org](https://docs.ros.org) (Humble); Articulated Robotics (YouTube); [docs.isaacsim.omniverse.nvidia.com](https://docs.isaacsim.omniverse.nvidia.com); [isaac-sim.github.io/IsaacLab](https://isaac-sim.github.io/IsaacLab).
- **AI / RL / CV:** Spinning Up in Deep RL (OpenAI); Ultralytics YOLOv8 docs; [colab.research.google.com](https://colab.research.google.com).
- **Cộng đồng:** [forum.xiaozhi.vn](https://forum.xiaozhi.vn) (Việt Nam); ROS Discourse & `r/robotics` (Quốc tế).
