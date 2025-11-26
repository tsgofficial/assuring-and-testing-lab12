# Лифтний FSM – Тест Кейсууд ба Сценариуд

## Тест Кейс 1 – Дээшээ дуудах

**Input:** CALL_UP(3)  
**Initial:** IDLE, 1-р давхар  
**Expected path:**  
IDLE → MOVING_UP → DOOR_OPEN → DOOR_CLOSING → IDLE

---

## Тест Кейс 2 – Доошоо дуудах

**Input:** CALL_DOWN(1)  
**Initial:** IDLE, 3-р давхар  
**Expected:**  
IDLE → MOVING_DOWN → DOOR_OPEN → DOOR_CLOSING → IDLE

---

## Тест Кейс 3 – Лифт дотороос давхар сонгох

**Input:** INSIDE_SELECT(2)  
**Initial:** IDLE, 1-р давхар  
**Expected:**  
IDLE → MOVING_UP → DOOR_OPEN → DOOR_CLOSING → IDLE

---

## Тест Кейс 4 – Хаалга нээлттэй үед хөдөлж болохгүй

**Initial:** DOOR_OPEN  
**Input:** CALL_UP(5)  
**Expected:**  
Төлөв **DOOR_OPEN хэвээр үлдэнэ**, хөдөлгөөн үүсэхгүй.

---

## Тест Кейс 5 – Олон хүсэлт дараалсан нөхцөл

**Inputs:** CALL_UP(3), CALL_DOWN(1)  
**Expected:**

1. IDLE → MOVING_UP → DOOR_OPEN → DOOR_CLOSING → IDLE
2. IDLE → MOVING_DOWN → DOOR_OPEN → DOOR_CLOSING → IDLE

---

## Тест Кейс 6 – Хаалга автоматаар хаагдах

**Initial:** DOOR_OPEN  
**Input:** DOOR_TIMEOUT  
**Expected:**  
DOOR_OPEN → DOOR_CLOSING → IDLE

---

# Сценари – Бүрэн гүйлгээ

**Нэг хэрэглэгч доороос лифт дуудан, лифтэнд сууж, дотороос өөр давхар сонгодог нөхцөл**

1. CALL_UP(1)
2. MOVING_DOWN → REACHED → DOOR_OPEN
3. DOOR_TIMEOUT → DOOR_CLOSING → IDLE
4. INSIDE_SELECT(5)
5. MOVING_UP → REACHED → DOOR_OPEN
6. DOOR_CLOSING → IDLE
