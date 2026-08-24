# Phân tích kết quả A/B Prompt

## Kết quả RAGAS

| Metric | Prompt V1 | Prompt V2 | Nhận xét |
|---|---:|---:|---|
| Faithfulness | 0.9725 | 0.9399 | V1 tốt hơn; cả hai vượt mục tiêu 0.8 và mốc thưởng 0.9. |
| Answer relevancy | 0.9122 | 0.7619 | V1 tập trung vào câu hỏi hơn rõ rệt. |
| Context recall | 1.0000 | 1.0000 | Retriever tìm được đầy đủ thông tin cần thiết ở cả hai phiên bản. |
| Context precision | 0.9450 | 0.9450 | Chất lượng context truy xuất tương đương vì hai phiên bản dùng cùng FAISS retriever. |

## Kết luận

Prompt V1 là lựa chọn tốt hơn cho hệ thống hiện tại. Ràng buộc trả lời ngắn gọn và trực tiếp giúp mô hình bám sát câu hỏi, nhờ đó đạt faithfulness và answer relevancy cao hơn. Prompt V2 yêu cầu câu trả lời có cấu trúc, giải thích và nêu giới hạn; yêu cầu này tạo câu trả lời dài hơn nên làm giảm answer relevancy, dù vẫn giữ faithfulness ở mức rất cao.

Vì hai prompt dùng chung knowledge base, chunking, embedding model và top-3 retriever, context recall và context precision gần như không thay đổi. Nếu ưu tiên trải nghiệm trả lời ngắn gọn, chính xác và ít lan man, nên triển khai V1; V2 phù hợp hơn khi người dùng cần diễn giải theo cấu trúc.
