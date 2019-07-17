---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246531"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Dołącza nagłówek biblioteki standardowe C \<stdlib.h > i dodaje skojarzone nazwy `std` przestrzeni nazw. Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<stdlib.h > nie zawiera typu **wchar_t**.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<cstdlib — >

**Namespace:** standardowe

## <a name="namespace-and-macros"></a>Makra i Namespace

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Działa tylko w specyfikacji

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funkcje rozpoczęcia i zakończenia

|Funkcja|Opis|
|-|-|
|[_Exit](#_exit)|Kończy program bez korzystania z destruktorów lub funkcji zarejestrowane.|
|[abort](#abort)|Kończy program bez korzystania z destruktorów.|
|[atexit](#atexit)|Funkcja rejestrów do kończenia działania programu.|
|[Zakończ](#exit)|Niszczy obiekty przy użyciu statycznego magazynu, a następnie zwraca kontroli i wątku.|
|[at_quick_exit](#at_quick_exit)|Funkcja rejestrów bez argumentów do kończenia działania programu.|
|[quick_exit](#quick_exit)|Funkcja rejestrów obiektami zachowanych do kończenia działania programu.|
|[getenv](#getenv)|Zobacz odwołanie do biblioteki standardowej C.|
|[system](#system)|Zobacz odwołanie do biblioteki standardowej C.|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Program jest zamykany, bez wykonywania destruktory dla obiektów automatyczny, wątek lub statycznym okresem magazynu i bez wywoływania przekazany do funkcji `atexit()`. Funkcja `_Exit` jest bezpieczna pod względem sygnału.

### <a name="abort"></a> Przerwij

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Uwagi

Program jest zamykany, bez wykonywania destruktory dla obiektów automatyczny, wątek lub statycznym okresem magazynu i bez wywoływania przekazany do funkcji `atexit()`. Funkcja `abort` jest bezpieczna pod względem sygnału.

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Wartość zwracana

Zero, jeśli rejestracja zakończy się powodzeniem, wartości zero, jeśli zakończy się niepowodzeniem.

#### <a name="remarks"></a>Uwagi

`at_quick_exit()` Funkcje rejestrowania funkcji wskazywany przez *func* można wywołać bez argumentów podczas `quick_exit` jest wywoływana. Ma ona nieokreślona czy wywołanie `at_quick_exit()` nie mają miejsce przed wszystkie wywołania do `quick_exit` zakończy się powodzeniem i `at_quick_exit()` funkcji nie wprowadzają wyścigu danych. Kolejność rejestracji może być nieokreślony Jeśli `at_quick_exit` została wywołana z więcej niż jeden wątek, a ponieważ `at_quick_exit` rejestracji różnią się od `atexit` rejestracji aplikacji może być konieczne wywoływanie obie funkcje rejestracji za pomocą Ten sam argument. Implementacja wspiera rejestracji funkcji co najmniej 32.

### <a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Uwagi

`atexit()` Funkcje rejestrowania funkcji wskazywany przez *func* można wywołać bez argumentów na zakończenie normalne programu. Ma ona nieokreślona czy wywołanie `atexit()` nie mają miejsce przed wywołaniem do `exit()` zakończy się powodzeniem i `atexit()` funkcji nie wprowadzają wyścigu danych. Implementacja wspiera rejestracji funkcji co najmniej 32.

#### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli rejestracja powiedzie się, wartość różną od zera, jeśli zakończy się niepowodzeniem.

### <a name="exit"></a> Zakończ

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Uwagi

Najpierw obiekty z okresem magazynu wątku i skojarzone z bieżącego wątku są niszczone.

Następnie obiekty ze statycznym okresem magazynu są niszczone, i funkcje zarejestrowany przez wywołanie metody `atexit` są wywoływane. Obiekty automatyczne nie są niszczone, w wyniku wywołania `exit()`. Jeśli formant opuszcza zarejestrowanej funkcji wywoływane przez `exit` ponieważ funkcja nie zapewnia obsługi zgłoszonego wyjątku `std::terminate()` nosi nazwę. Funkcja jest wywoływana dla za każdym razem, gdy jest on zarejestrowany. Obiekty z automatycznym okresem magazynu są niszczone w programie, którego główna funkcja nie zawiera automatyczne obiektów i wykonuje wywołanie `exit()`. Kontrolki można przenieść bezpośrednio do funkcji main, zostanie zgłoszony wyjątek, który zostanie przechwycony w głównym oknie.

Następnie otwórz wszystkie strumienie C (zgodnie z sygnatury funkcji zadeklarowanych w — za pośrednictwem <cstdio>) przy użyciu niezapisanych buforowane dane są wyczyszczone, wszystkie otwarte C strumienie zostały zamknięte, a wszystkie pliki tworzone przez wywołanie `tmpfile()` są usuwane.

Na koniec zwróceniem sterowania do środowiska hosta. Jeśli stan ma wartość zero lub EXIT_SUCCESS, zwracany jest zakończenie pomyślne stanu w formie zdefiniowanych w implementacji. Jeśli stan jest EXIT_FAILURE, zwracany jest zakończenie niepowodzeniem stanu w formie zdefiniowanych w implementacji. W przeciwnym razie zwrócony kod stanu jest zdefiniowane w implementacji.

### <a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Funkcje zarejestrowane w wyniku wywołania `at_quick_exit` są wywoływane w odwrotnej kolejności ich rejestracji, z tą różnicą, że funkcja jest wywoływana po wcześniej zarejestrowane dowolnej funkcji, które już wywołano w chwili rejestracji. Obiekty nie są niszczone w wyniku wywołania `quick_exit`. Jeśli formant opuszcza zarejestrowanej funkcji wywoływane przez `quick_exit` ponieważ funkcja nie zapewnia obsługi zgłoszonego wyjątku `std::terminate()` nosi nazwę. Funkcja zarejestrować za pomocą `at_quick_exit` zostanie wywołany przez wątek, który wywołuje `quick_exit`, który może być innym wątku niż ten, który jest zarejestrowany, więc zarejestrowany funkcji nie należy polegać na tożsamości obiektów z okresem magazynu wątku. Po wywołaniu funkcji zarejestrowanych `quick_exit` musi wywołać `_Exit(status)`. Bufory standardowego pliku nie są opróżniane. Funkcja `quick_exit` jest bezpieczna sygnał, gdy funkcje zarejestrowane w usłudze `at_quick_exit` są.

### <a name="system"></a> System

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funkcje alokacji pamięci

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

#### <a name="remarks"></a>Uwagi

Funkcje te mają semantykę określony w standardowej bibliotece C.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Ciąg znaków wielobajtowych / szerokiej i funkcje konwersji znaków

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Uwagi

Funkcje te mają semantykę określony w standardowej bibliotece C.

## <a name="algorithm-functions"></a>Funkcje algorytmiczne

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Uwagi

Funkcje te mają semantykę określony w standardowej bibliotece C.

## <a name="low-quality-random-number-generation-functions"></a>Funkcje generowania liczb losowych niskiej jakości

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Uwagi

Funkcje te mają semantykę określony w standardowej bibliotece C.

## <a name="absolute-values"></a>Wartości bezwzględne

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Uwagi

Funkcje te mają semantykę określony w standardowej bibliotece C.

## <a name="functions"></a>Funkcje

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
