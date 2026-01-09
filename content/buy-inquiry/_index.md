---
title: "매입문의"
---

매입 문의는 아래 폼으로 접수해주세요. (사진 업로드 가능)

<div id="buy-lock" class="p-4 border rounded-4 bg-light">
  <h3 class="fw-bold mb-2">비밀번호 확인</h3>
  <p class="text-muted mb-3">매입문의 페이지는 비밀번호 입력 후 이용할 수 있습니다.</p>

  <div class="d-flex gap-2">
    <input id="buy-pass" type="password" class="form-control" placeholder="비밀번호 입력">
    <button id="buy-unlock" class="btn btn-dark">확인</button>
  </div>

  <div id="buy-msg" class="text-danger small mt-2" style="display:none;">비밀번호가 올바르지 않습니다.</div>
</div>

<div id="buy-form" style="display:none;" class="mt-4">
  <div class="ratio ratio-16x9">
    <iframe
      src="FORM_EMBED_URL"
      frameborder="0"
      marginheight="0"
      marginwidth="0">
      로딩 중…
    </iframe>
  </div>

  <p class="text-muted small mt-2">
    * 파일 업로드는 폼 설정에 따라 Google 로그인이 필요할 수 있습니다.
  </p>
</div>

<script>
  // ⚠️ 간단 잠금(강한 보안 아님). 진짜 보안이 필요하면 Netlify Identity/Access로 보호 추천.
  const PASS = "1234"; // <- 여기 비밀번호 바꾸기
  const KEY = "buy_inquiry_unlocked";

  function showForm() {
    document.getElementById("buy-lock").style.display = "none";
    document.getElementById("buy-form").style.display = "block";
  }

  if (sessionStorage.getItem(KEY) === "1") showForm();

  document.getElementById("buy-unlock").addEventListener("click", () => {
    const v = document.getElementById("buy-pass").value;
    if (v === PASS) {
      sessionStorage.setItem(KEY, "1");
      showForm();
    } else {
      document.getElementById("buy-msg").style.display = "block";
    }
  });
</script>
