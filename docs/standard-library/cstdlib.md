---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 1b20e13a43c5d223332af70a91e096cedc284a43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230055"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Zawiera nagłówek standardowej biblioteki C \<stdlib.h> i dodaje skojarzone nazwy do `std` przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<stdlib.h>nie zawiera typu **`wchar_t`** .

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<cstdlib>

**Przestrzeń nazw:** std

## <a name="namespace-and-macros"></a>Przestrzeń nazw i makra

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

## <a name="exposition-only-functions"></a>Funkcje tylko do dokumentacji

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funkcje uruchamiania i kończenia

|Funkcja|Opis|
|-|-|
|[_Exit](#_exit)|Kończy program bez używania destruktorów ani zarejestrowanych funkcji.|
|[przerwij](#abort)|Kończy program bez używania destruktorów.|
|[atexit](#atexit)|Rejestruje funkcję do zakończenia programu.|
|[Opuść](#exit)|Niszczy obiekty ze wątkiem i magazynem statycznym, a następnie zwraca kontrolę.|
|[at_quick_exit](#at_quick_exit)|Rejestruje funkcję bez argumentów do zakończenia programu.|
|[quick_exit](#quick_exit)|Rejestruje funkcję z zachowanymi obiektami do zakończenia działania programu.|
|[getenv](#getenv)|Zobacz standardowe informacje o bibliotece języka C.|
|[system](#system)|Zobacz standardowe informacje o bibliotece języka C.|

### <a name="_exit"></a><a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Program zostaje zakończony bez wykonywania destruktorów dla obiektów typu automatyczny, wątek lub statyczny czas przechowywania oraz bez wywoływania funkcji zakończonych do `atexit()` . Funkcja `_Exit` jest w bezpiecznym sygnale.

### <a name="abort"></a><a name="abort"></a>Anuluj

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Uwagi

Program zostaje zakończony bez wykonywania destruktorów dla obiektów typu automatyczny, wątek lub statyczny czas przechowywania oraz bez wywoływania funkcji zakończonych do `atexit()` . Funkcja `abort` jest w bezpiecznym sygnale.

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Wartość zwracana

Zero, jeśli rejestracja powiedzie się, jeśli nie powiedzie się.

#### <a name="remarks"></a>Uwagi

Funkcja `at_quick_exit()` rejestruje funkcję funkcji, *func*która jest wywoływana bez argumentów, gdy `quick_exit` jest wywoływana. Wywołanie `at_quick_exit()` , które nie występuje, zanim wszystkie wywołania programu `quick_exit` mogą się nie powieść. `at_quick_exit()`Funkcje nie wprowadzają wyścigu do danych. Kolejność rejestracji może być nieokreślona, jeśli `at_quick_exit` została wywołana z więcej niż jednego wątku. Ponieważ `at_quick_exit` rejestracje różnią się od `atexit` rejestracji, aplikacje mogą wymagać wywołania obu funkcji rejestracji przy użyciu tego samego argumentu. MSVC obsługuje rejestrację co najmniej 32 funkcji.

### <a name="atexit"></a><a name="atexit"></a>atexit —

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Uwagi

`atexit()`Funkcja rejestruje funkcję wskazywaną przez *Func* , która ma zostać wywołana bez argumentów przy normalnym zakończeniu działania programu. Wywołanie `atexit()` , które nie występuje, przed wywołaniem metody `exit()` może się nie powieść. `atexit()`Funkcje nie wprowadzają wyścigu do danych.

#### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli rejestracja kończy się niepowodzeniem, jeśli nie powiedzie się.

### <a name="exit"></a><a name="exit"></a>Opuść

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Uwagi

Najpierw obiekty z okresem przechowywania wątków i skojarzone z bieżącym wątkiem są niszczone.

Następnie obiekty ze statycznym okresem przechowywania są niszczone, a funkcje zarejestrowane przez wywołanie `atexit` są wywoływane. Obiekty automatyczne nie są niszczone, gdy `exit()` jest wywoływana. Jeśli kontrolka opuszcza zarejestrowana funkcja wywołana przez `exit` , ponieważ funkcja nie dostarcza procedury obsługi dla zgłoszonego wyjątku, `std::terminate()` jest wywoływana. Funkcja jest wywoływana raz przy każdym zarejestrowaniu. Obiekty z automatycznym okresem magazynu są niszczone w programie, którego `main` Funkcja nie zawiera obiektów automatycznych i wykonuje wywołanie metody `exit()` . Kontrolę można przenieść bezpośrednio do takiej `main` funkcji, zwracając wyjątek, który jest przechwytywany `main` .

Następnie wszystkie otwarte strumienie języka C (zgodnie z opisem w temacie \<cstdio> ) z niezapisanymi danymi buforowanymi są opróżniane, wszystkie otwarte strumienie c są zamknięte, a wszystkie pliki utworzone przez wywołanie `tmpfile()` są usuwane.

Na koniec kontrola jest zwracana do środowiska hosta. Gdy *stan* ma wartość zero lub EXIT_SUCCESS, zwracany jest formularz o stanie pomyślne zakończenie stanu. MSVC zwraca wartość zero. Jeśli *stan* jest EXIT_FAILURE, MSVC zwraca wartość 3. W przeciwnym razie MSVC zwraca wartość parametru *stanu* .

### <a name="getenv"></a><a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Uwagi

Ogólnie rzecz biorąc, funkcje zarejestrowane przez wywołania `at_quick_exit` są wywoływane w odwrotnej kolejności rejestracji. Ta kolejność nie ma zastosowania do funkcji zarejestrowanych po zarejestrowaniu innych funkcji, które zostały już wywołane. Gdy jest wywoływana, żadne obiekty nie są niszczone `quick_exit` . Jeśli kontrolka opuszcza zarejestrowana funkcja wywołana przez `quick_exit` , ponieważ funkcja nie dostarcza procedury obsługi dla zgłoszonego wyjątku, `std::terminate()` jest wywoływana. Funkcja zarejestrowana za pośrednictwem `at_quick_exit` jest wywoływana przez wątek wywołujący `quick_exit` , który może być innym wątkiem niż ten, który go zarejestrował. Oznacza to, że zarejestrowane funkcje nie należy polegać na tożsamości obiektów, które mają czas trwania magazynu wątków. Po wywołaniu zarejestrowanych funkcji `quick_exit` wywołania `_Exit(status)` . Standardowe bufory plików nie są opróżniane. Funkcja `quick_exit` jest bezpieczna sygnałem, gdy funkcje zarejestrowane w `at_quick_exit` są.

### <a name="system"></a><a name="system"></a>systemami

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funkcje alokacji pamięci

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C. MSVC nie obsługuje `aligned_alloc` funkcji. C11 określone `aligned_alloc()` w sposób, który jest niezgodny z implementacją firmy Microsoft `free()` , czyli, która `free()` musi być w stanie obsługiwać wysoce wyrównane alokacje.

## <a name="numeric-string-conversions"></a>Konwersje ciągów numerycznych

```cpp
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

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>Funkcje konwersji ciągów wielobajtowych/szerokich i znaków

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="algorithm-functions"></a>Funkcje algorytmu

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="low-quality-random-number-generation-functions"></a>Funkcje generowania liczb losowych o niskiej jakości

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

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
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="integer-division"></a>Dzielenie liczb całkowitych

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Uwagi

Te funkcje mają semantykę określoną w standardowej bibliotece języka C.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
