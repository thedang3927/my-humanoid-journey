Bài tập 4: Trả lời 3 câu hỏi vào file docs/00-notes.md.
• 1. DoF (Degree of Freedom) là gì? Tại sao humanoid cần nhiều DoF?
• 2. Sim-to-real gap là gì? Tại sao nó là vấn đề số 1?
• 3. Tại sao chiến lược “mô phỏng là chính, phần cứng là proxy” lại phù hợp? Nêu ít
nhất 2 lý do.
Trả lời ngắn gọn (3–5 dòng/câu), tập trung vào bản chất.

-----------------------------------------
Trả lời:
1. DoF (Degree of Freedom):
    - Là bậc tự do, tham số chuyển động độc lập.
    - Các khớp để xoay/tịnh tiến được tính là DoF.
    - Otto Ninja sẽ có 4 DoF: 2 DoF ở hông và 2 DoF ở bàn chân.
    - Humanoid Robot thật có khoảng 30-50 DoF để cân bằng, di chuyển, tương tác, dự phòng, nên sẽ khó kiểm soát và phối hợp hơn Otto Ninja.
    
2. Sim-to-real gap:
    - Là khoảng cách từ mô phỏng trên app mô phỏng như Isaac Sim, Isaac Lab đến đời thực.
    - Cụ thể hơn là việc đưa policy chạy được trên app mô phỏng ra ngoài chạy thực tế trên một robot vật lý thật sẽ khó và là vấn đề số 1 của ngành, vì:
        + Ngoài đời sẽ có sự khác biệt nhất định về ma sát, khối lượng cần điều chỉnh, độ trễ của cảm biến.
        + Việc điều chỉnh để robot chạy được thật ở ngoài đời yêu cầu nhiều yếu tố về kỹ năng và chuyên môn hơn.

3. Chiến lược "Mô phỏng là chính, phần cứng là proxy" phù hợp, vì:
    - Humanoid Robot thương mại thật đang có trên thị trường quá đắt so với một sinh viên, từ 50.000 đến 500.000 USD. 
    - DIY (Do It Yourself) Humanoid Robot tối thiểu cũng tốn hàng chục triệu đồng.
    - Mô phỏng trên app mô phỏng như Isaac Lab, Isaac Sim giúp sinh viên thể hiện tư duy sử dụng phần mềm tốt, thiết kế, mô phỏng trước khi đưa vào thực tế để tối ưu kết quả.
    - Phần cứng vẫn nên có như proxy, như Otto Ninja, giúp sinh viên thể hiện kỹ năng chuyên môn và kỹ thuật làm việc trên vật liệu vật lý thực sự chứ không chỉ là mô phỏng lý thuyết.
    - Tối ưu hóa khả năng thuyết phục thầy/cô, bạn bè, nhà đầu tư trong quá trình học tập, xin học bổng, xin quỹ phát triển dự án...
