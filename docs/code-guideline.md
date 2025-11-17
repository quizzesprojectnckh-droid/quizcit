\- Để cho team có thể làm project một cách có nhất quán cũng như dễ fix lỗi thì ta nên có chung một bộ quy tắc trong code để dễ review xem code qua lại.

**1\. Về quy tắc code:**  
Áp dụng MERN (Mongoose, Expressjs, Reactjs, Nodejs) cho cả full stack, trên frontend style bằng tailwindcss kết hợp với css cho những style chi tiết cần thiết.  
Dùng camelCase cho tên hàm, biến, tất nhiên là tên component vẫn phải là PascalCase (bắt buộc của react).  
Code prettier: [Prettier (VSCode)](https://open-vsx.org/vscode/item?itemName=esbenp.prettier-vscode). Nên bật luôn format on save ( Settings \-\> format on save)  
Cấu trúc thư mục: ( Có thể bổ sung thêm )  
Root  
├── backend  
│ ├── configs  
│ ├── controllers  
│ ├── middlewares  
│ ├── models  
│ ├── routes  
│ ├── services  
│ └── utils  
└── frontend  
 └── quizcit  
 ├── public  
 └── src  
 ├── api  
 ├── assets  
 ├── components  
 ├── hooks  
 ├── pages  
 ├── store  
 └── utils

\+ Giải thích cấu trúc thư mục:  
**\- backend:**  
configs: chứa các file cấu hình của server, ví dụ: database connection, environment variables, JWT secret, logger config…  
controllers: xử lý logic khi nhận request từ client, gọi service / model và trả response.  
middlewares: chứa các middleware cho Express, ví dụ: authentication, authorization, logging, error handling.  
models: chứa các schema của mongodb  
routes: định nghĩa route endpoints, ánh xạ tới controller tương ứng của chúng.  
services: chứa các business logic, cái controller chỉ nhận request, validate nos rồi gọi service xử lý cái request, sau đó mới trả response.  
utils: các helper function dùng chung.  
**\- frontend/quizcit:** folder chứa project react  
src/api: chứa các hàm gọi API từ backend.  
src/assets: chứa hình ảnh, icon, font,...  
src/components: chứa các component có khả năng tái sử dụng  
src/hooks: chứa các custom hooks  
src/pages: chứa các page component tương ứng với từng route.  
src/store: chứa quản lý state toàn cục của redux hoặc mấy cái tương tự nếu có  
src/utils: các helper function dùng chung.

**2\. Về version control:**  
**\*\*KHÔNG push .env lên trên github**  
\- Sử dụng github làm version control chính:  
\+ Về commit, không nên commit quá nhiều việc cùng lúc, nên giữ commit nhất quán về công việc, ví dụ chỉ commit mỗi lần 1 tính năng.  
\+ Về branch, khi phát triển, mỗi tính năng cần có một branch riêng ví dụ feature/login-page. Để merge branch tính năng vào branch chính, cần đặt pull request để xem qua code rồi mới merge ( cái này có thể bỏ qua trong giai đoạn đầu, khi app deploy rồi mới làm cũng được ).  
**3\. Về môi trường code:**  
Cái này tự do, muốn làm trên vscode hay jetbrains gì cũng được, miễn là .gitignore và .env đồng nhất với project.  
**4\. Về sử dụng GPT, Gemini, etc...:**  
Không cấm nhưng khi dùng phải đảm bảo cấu trúc của hệ thống được đề ra, không thêm, bớt tính năng nào của hệ thống mà không có bàn trước với team để cập nhật trên hệ thống. Cái này để né lỗi, tin tui đi anh em cái này quan trọng dữ lắm, xài GPT không để ý là lạc đề với hệ thống đó.
