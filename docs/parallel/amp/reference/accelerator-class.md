---
title: accelerator — Klasa
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 2045d2d1c6a848378ac55114b61177d386b14fab
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523926"
---
# <a name="accelerator-class"></a>accelerator — Klasa

Akcelerator to zdolność sprzętu zoptymalizowana pod kątem przetwarzania równoległego danych. Akcelerator może być urządzeniem podłączonym do magistrali PCIe (na przykład GPU) lub może być rozszerzonym zbiorem głównego CPU instrukcji.

## <a name="syntax"></a>Składnia

```
class accelerator;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[accelerator Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator` klasy.|
|[~ accelerator — destruktor](#ctor)|Niszczy `accelerator` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[create_view —](#create_view)|Tworzy i zwraca `accelerator_view` obiekt w tym akceleratorze.|
|[get_all](#get_all)|Zwraca wektor `accelerator` obiektami, które reprezentują wszystkie dostępne akceleratory.|
|[get_auto_selection_view](#get_auto_selection_view)|Zwraca automatyczny wybór `accelerator_view`.|
|[get_dedicated_memory](#get_dedicated_memory)|Zwraca ilość pamięci dedykowanej dla `accelerator`, w kilobajtach.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Zwraca domyślny [access_type](concurrency-namespace-enums-amp.md#access_type) dla buforów utworzonych w tym akceleratorze.|
|[get_default_view](#get_default_view)|Zwraca domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator`.|
|[get_description](#get_description)|Zwraca krótki opis `accelerator` urządzenia.|
|[get_device_path](#get_device_path)|Zwraca ścieżkę urządzenia.|
|[get_has_display](#get_has_display)|Określa, czy `accelerator` jest dołączony do ekranu.|
|[get_is_debug](#get_is_debug)|Określa, czy `accelerator` ma włączoną warstwę debugowanie dla obszernego raportowania błędów.|
|[get_is_emulated —](#get_is_emulated)|Określa, czy `accelerator` jest emulowany.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Określa, czy `accelerator` obsługuje pamięć współużytkowaną|
|[get_supports_double_precision](#get_supports_double_precision)|Określa, czy `accelerator` jest dołączony do ekranu.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Określa, czy `accelerator` ma ograniczoną obsługę działań matematycznych podwójnej precyzji.|
|[get_version](#get_version)|Zwraca wersję `accelerator`.|
|[set_default](#set_default)|Zwraca ścieżkę domyślnego akceleratora.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Ustawia domyślny Procesor [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic oraz niejawnych alokacji pamięci dokonanych dla tego `accelerator`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porównuje ten `accelerator` obiekt z innym i zwraca **false** jeśli są one takie same; w przeciwnym razie zwraca **true**.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `accelerator` obiektu do wskazanego.|
|[operator==](#operator_eq_eq)|Porównuje ten `accelerator` obiekt z innym i zwraca **true** jeśli są one takie same; w przeciwnym razie zwraca **false**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Pobiera stałą typu string dla CPU `accelerator`.|
|[dedicated_memory](#dedicated_memory)|Pobiera ilość pamięci dedykowanej dla `accelerator`, w kilobajtach.|
|[default_accelerator](#default_accelerator)|Pobiera stałą typu string dla domyślnego `accelerator`.|
|[default_cpu_access_type](#default_cpu_access_type)|Pobiera lub ustawia domyślny Procesor [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic oraz niejawnych alokacji pamięci dokonanych dla tego `accelerator`.|
|[default_view —](#default_view)|Pobiera domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator`.|
|[Opis elementu](#description)|Pobiera krótki opis `accelerator` urządzenia.|
|[device_path](#device_path)|Pobiera ścieżkę urządzenia.|
|[direct3d_ref](#direct3d_ref)|Pobiera stałą typu string dla odwołania Direct3D `accelerator`.|
|[direct3d_warp](#direct3d_warp)|Pobiera stałą typu ciąg `accelerator` obiektu służące do wykonywania kodu C++ AMP na wielordzeniowych procesorach, które używają rozszerzenia SSE (Streaming SIMD).|
|[has_display —](#has_display)|Pobiera wartość logiczną, wskazującą, czy `accelerator` jest dołączony do ekranu.|
|[is_debug](#is_debug)|Wskazuje, czy `accelerator` ma włączoną warstwę debugowanie dla obszernego raportowania błędów.|
|[is_emulated —](#is_emulated)|Wskazuje, czy `accelerator` jest emulowany.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Wskazuje, czy `accelerator` obsługuje pamięć współużytkowaną.|
|[supports_double_precision](#supports_double_precision)|Wskazuje, czy akcelerator obsługuje matematykę o podwójnej precyzji.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Wskazuje, czy akcelerator ma ograniczoną obsługę działań matematycznych podwójnej precyzji.|
|[version](#version)|Pobiera wersję `accelerator`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`accelerator`

## <a name="remarks"></a>Uwagi

Akcelerator to zdolność sprzętu zoptymalizowana pod kątem przetwarzania równoległego danych. Akcelerator jest często dyskretnym GPU, ale może też być wirtualne jednostki po stronie hosta, takie jak urządzenie DirectX REF, WARP (urządzenie po stronie procesora CPU, które jest przyspieszane za pomocą instrukcji SSE) lub samym procesorem.

Można skonstruować `accelerator` obiektu przez wyliczenie dostępnych urządzeń lub uzyskanie domyślnego urządzenia, odwołania do urządzenia lub urządzenia WARP.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** współbieżności

##  <a name="dtor"></a> </a> ~ accelerator

Niszczy `accelerator` obiektu.

```
~accelerator();
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="ctor"></a> Akcelerator

Inicjuje nowe wystąpienie klasy [accelerator — klasa](accelerator-class.md).

```
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Device_path*<br/>
Ścieżka urządzenia fizycznego.

*_Inne*<br/>
Akcelerator do skopiowania.

##  <a name="cpu_accelerator"></a> cpu_accelerator —

Pobiera stałą typu string dla akceleratora Procesora.

```
static const wchar_t cpu_accelerator[];
```

##  <a name="create_view"></a> create_view —

Tworzy i zwraca `accelerator_view` obiekt w tym akceleratorze, za pomocą określonego trybu kolejkowania. Jeśli nie określono tryb kolejkowania, nowa `accelerator_view` używa [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) tryb kolejkowania.

```
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*qmode*<br/>
Tryb kolejkowania.

### <a name="return-value"></a>Wartość zwracana

Nowy `accelerator_view` obiekt w tym akceleratorze, za pomocą określonego trybu kolejkowania.

##  <a name="dedicated_memory"></a> dedicated_memory —

Pobiera ilość pamięci dedykowanej dla `accelerator`, w kilobajtach.

```
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

##  <a name="default_accelerator"></a> default_accelerator —

Pobiera stałą typu string dla domyślnego `accelerator`.

```
static const wchar_t default_accelerator[];
```

##  <a name="default_cpu_access_type"></a> default_cpu_access_type

Wartość domyślna procesora [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic oraz niejawnych alokacji pamięci dokonanych dla tego `accelerator`.

```
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

##  <a name="default_view"></a> default_view —

Pobiera domyślny widok akceleratora, który jest skojarzony z `accelerator`.

```
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

##  <a name="description"></a> Opis elementu

Pobiera krótki opis `accelerator` urządzenia.

```
__declspec(property(get= get_description)) std::wstring description;
```

##  <a name="device_path"></a> device_path

Pobiera ścieżkę do akceleratora. Ścieżka jest unikatowa w systemie.

```
__declspec(property(get= get_device_path)) std::wstring device_path;
```

##  <a name="direct3d_ref"></a> direct3d_ref —

Pobiera stałą typu string dla akceleratora odwołanie Direct3D.

```
static const wchar_t direct3d_ref[];
```

##  <a name="direct3d_warp"></a> direct3d_warp —

Pobiera stałą typu ciąg `accelerator` obiektu służące do wykonywania kodu C++ AMP na wielordzeniowych procesorach przy użyciu rozszerzenia SSE (Streaming SIMD).

```
static const wchar_t direct3d_warp[];
```

##  <a name="get_all"></a> get_all

Zwraca wektor `accelerator` obiektami, które reprezentują wszystkie dostępne akceleratory.

```
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Wartość zwracana

Wektor dostępnych akceleratorów

##  <a name="get_auto_selection_view"></a> get_auto_selection_view

Zwraca Wybór auto accelerator_view, który, gdy określony jako cel parallel_for_each daje w accelerator_view dla wykonania jądra parallel_for_each automatycznie wybierany w czasie wykonywania. Do innych celów widok akceleratora zwracany przez tę metodę jest taki sam jak domyślny widok akceleratora domyślnego

```
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Wartość zwracana

Accelerator_view wyboru automatycznego.

##  <a name="get_dedicated_memory"></a> get_dedicated_memory —

Zwraca ilość pamięci dedykowanej dla `accelerator`, w kilobajtach.

```
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Wartość zwracana

Ilość pamięci dedykowanej dla `accelerator`, w kilobajtach.

##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type

Pobiera domyślny atrybut access_type procesora dla buforów utworzonych w tym akceleratorze

```
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny access_type do procesora dla buforów utworzonych w tym akceleratorze.

##  <a name="get_default_view"></a> get_default_view —

Zwraca domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator`.

```
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość domyślna `accelerator_view` obiekt, który jest skojarzony z `accelerator`.

##  <a name="get_description"></a> get_description —

Zwraca krótki opis `accelerator` urządzenia.

```
std::wstring get_description() const;
```

### <a name="return-value"></a>Wartość zwracana

Krótki opis `accelerator` urządzenia.

##  <a name="get_device_path"></a> get_device_path

Zwraca ścieżkę akceleratora. Ścieżka jest unikatowa w systemie.

```
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka wystąpienia unikatowych urządzeń w całym systemie.

##  <a name="get_has_display"></a> get_has_display —

Zwraca wartość logiczną wskazującą, czy `accelerator` może zapewniać dane wyjściowe do wyświetlania.

```
bool get_has_display() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `accelerator` może zapewniać dane wyjściowe na wyświetlacz; w przeciwnym razie **false**.

##  <a name="get_is_debug"></a> get_is_debug —

Określa, czy `accelerator` ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `accelerator` ma włączoną warstwę debugowanie dla obszernego raportowania błędów. W przeciwnym razie **false**.

##  <a name="get_is_emulated"></a> get_is_emulated —

Określa, czy `accelerator` jest emulowany.

```
bool get_is_emulated() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `accelerator` jest emulowany. W przeciwnym razie **false**.

##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory

Zwraca wartość logiczną wskazującą, czy akcelerator obsługuje pamięć dostępną zarówno akceleratora, jak i procesora CPU.

```
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli akcelerator obsługuje Procesora udostępniony pamięci; w przeciwnym razie **false**.

##  <a name="get_supports_double_precision"></a> get_supports_double_precision

Zwraca wartość, należy pomnożyć wartość logiczną, wskazującą, czy akcelerator obsługuje matematykę o podwójnej precyzji, w tym zespolone Dodaj (FMA), dzielenie, odwracanie i operację rzutowania pomiędzy **int** i **double**

```
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli akcelerator obsługuje matematykę o podwójnej precyzji; w przeciwnym razie **false**.

##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision

Zwraca wartość logiczną wskazującą, czy akcelerator ma ograniczoną obsługę matematykę o podwójnej precyzji. Jeśli akcelerator obsługuje tylko ograniczone, połączone funkcjami wielokrotnie Dodaj (FMA), dzielenie, odwracanie i operację rzutowania pomiędzy **int** i **double** nie są obsługiwane.

```
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli akcelerator ma ograniczoną obsługę matematykę o podwójnej precyzji; w przeciwnym razie **false**.

##  <a name="get_version"></a> get_version —

Zwraca wersję `accelerator`.

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja `accelerator`.

##  <a name="has_display"></a> has_display —

Pobiera wartość logiczną, wskazującą, czy `accelerator` może zapewniać dane wyjściowe do wyświetlania.

```
__declspec(property(get= get_has_display)) bool has_display;
```

##  <a name="is_debug"></a> is_debug —

Pobiera wartość logiczną, wskazującą, czy `accelerator` ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="is_emulated"></a> is_emulated —

Pobiera wartość logiczną, wskazującą, czy `accelerator` jest emulowany.

```
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

##  <a name="operator_neq"></a> operator! =

Porównuje ten `accelerator` obiekt z innym i zwraca **false** jeśli są one takie same; w przeciwnym razie zwraca **true**.

```
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**FALSE** Jeśli dwa `accelerator` obiekty są takie same; w przeciwnym razie **true**.

##  <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego `accelerator` obiektu do wskazanego.

```
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `accelerator` obiektu.

##  <a name="operator_eq_eq"></a> operator ==

Porównuje ten `accelerator` obiekt z innym i zwraca **true** jeśli są one takie same; w przeciwnym razie zwraca **false**.

```
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli drugi `accelerator` obiekt jest taki sam jak ten `accelerator` obiektu; w przeciwnym razie **false**.

##  <a name="set_default"></a> set_default

Ustawia akcelerator domyślny, który ma być używany dla każdej operacji, która niejawnie wykorzystuje akcelerator domyślny. Metoda ta powiedzie się tylko, jeśli domyślny akcelerator wybrany nie został już użyty w operacji, która niejawnie wykorzystuje akcelerator domyślny

```
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parametry

*Ścieżka _wywołania*<br/>
Ścieżka do akceleratora.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wywołanie powiedzie się i wyznaczy akcelerator domyślny. W przeciwnym razie **false**.

##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type

Ustaw domyślny access_type do procesora dla tablic utworzonych w tym akceleratorze lub dla alokacji pamięci niejawnej, jako część widoków array_views dostępnych dostępne w tym akceleratorze. Metoda ta powiedzie się tylko, jeśli default_cpu_access_type dla akceleratora nie był jeszcze nadpisany przez poprzednie wywołanie tej metody, a wybrane środowisko uruchomieniowe default_cpu_access_type dla tego akceleratora nie jeszcze został użyty do przydzielania tablicy lub przydzielania pamięci niejawnej tworzącej kopię array_view dostępne w tym akceleratorze.

```
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parametry

*_Default_cpu_access_type*<br/>
Domyślny access_type do procesora ma być używany dla alokacji pamięci tablica/array_view w tym akceleratorze.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna wskazująca, jeśli domyślny access_type cpu dla akceleratora została ustawiona pomyślnie.

##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory

Pobiera wartość Boolean wskazującą czy `accelerator` obsługuje pamięć współużytkowaną.

```
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

##  <a name="supports_double_precision"></a> supports_double_precision

Pobiera wartość logiczną, wskazującą, czy akcelerator obsługuje matematykę o podwójnej precyzji.

```
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision

Pobiera wartość logiczną, wskazującą, czy akcelerator ma ograniczoną obsługę matematykę o podwójnej precyzji. Jeśli akcelerator obsługuje tylko ograniczone, połączone funkcjami wielokrotnie Dodaj (FMA), dzielenie, odwracanie i operację rzutowania pomiędzy `int` i `double` nie są obsługiwane.

```
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

##  <a name="version"></a> Wersja

Pobiera wersję `accelerator`.

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="dtor"></a> </a> ~ accelerator_view

Niszczy [accelerator_view](accelerator-view-class.md) obiektu.

```
~accelerator_view();
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="accelerator"></a> Akcelerator

Pobiera `accelerator` dla obiektu [accelerator_view](accelerator-view-class.md) obiektu.

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

##  <a name="ctor"></a> accelerator_view

Inicjuje nowe wystąpienie klasy [accelerator_view](accelerator-view-class.md) przez skopiowanie istniejącego `accelerator_view` obiektu.

```
accelerator_view(const accelerator_view& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiektu do skopiowania.

##  <a name="create_marker"></a> create_marker

Zwraca stan w przyszłości do śledzenia wykonania wszystkich poleceń dotychczas przekazanych do tego `accelerator_view` obiektu.

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Wartość zwracana

Stan w przyszłości do śledzenia wykonania wszystkich poleceń dotychczas przekazanych do tego `accelerator_view` obiektu.

##  <a name="flush"></a> Flush

Przesyła wszystkie oczekujące polecenia w kolejce do [accelerator_view](accelerator-view-class.md) obiektu do akceleratora do wykonania.

```
void flush();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `void`.

##  <a name="get_accelerator"></a> get_accelerator —

Zwraca `accelerator` dla obiektu [accelerator_view](accelerator-view-class.md) obiektu.

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Wartość zwracana

`accelerator` Dla obiektu `accelerator_view` obiektu.

##  <a name="get_is_auto_selection"></a> get_is_auto_selection

Zwraca wartość logiczną wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przekazywany do [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator; w przeciwnym razie **false**.

##  <a name="get_is_debug"></a> get_is_debug —

Zwraca wartość logiczną wskazującą, czy [accelerator_view](accelerator-view-class.md) obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która wskazuje, czy `accelerator_view` obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

##  <a name="get_queuing_mode"></a> get_queuing_mode

Zwraca tryb kolejkowania dla [accelerator_view](accelerator-view-class.md) obiektu.

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb kolejkowania dla `accelerator_view` obiektu.

##  <a name="get_version"></a> get_version —

Zwraca wersję [accelerator_view](accelerator-view-class.md).

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja `accelerator_view`.

##  <a name="is_auto_selection"></a> is_auto_selection

Pobiera wartość logiczną, wskazującą, czy środowisko wykonawcze automatycznie wybiera odpowiedni akcelerator, gdy accelerator_view jest przekazywany do [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

##  <a name="is_debug"></a> is_debug —

Pobiera wartość logiczną, wskazującą, czy [accelerator_view](accelerator-view-class.md) obiekt ma włączoną warstwę debugowanie dla obszernego raportowania błędów.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="operator_neq"></a> operator! =

Porównuje ten [accelerator_view](accelerator-view-class.md) obiekt z innym i zwraca `false` jeśli są one takie same; w przeciwnym razie zwraca `true`.

```
bool operator!= (const accelerator_view& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**FALSE** Jeśli dwa obiekty są takie same; w przeciwnym razie **true**.

##  <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego [accelerator_view](accelerator-view-class.md) obiektu do wskazanego.

```
accelerator_view& operator= (const accelerator_view& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zmodyfikowanego `accelerator_view` obiektu.

##  <a name="operator_eq_eq"></a> operator ==

Porównuje ten [accelerator_view](accelerator-view-class.md) obiekt z innym i zwraca **true** jeśli są one takie same; w przeciwnym razie zwraca **false**.

```
bool operator== (const accelerator_view& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`accelerator_view` Obiekt do porównania z tym kontem.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

##  <a name="queuing_mode"></a> queuing_mode

Pobiera tryb kolejkowania dla [accelerator_view](accelerator-view-class.md) obiektu.

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

##  <a name="version"></a> Wersja

Pobiera wersję [accelerator_view](accelerator-view-class.md).

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="wait"></a> Czekaj

Czeka, aż wszystkie polecenia przesłane do [accelerator_view](accelerator-view-class.md) obiektu, aby zakończyć.

```
void wait();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `void`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
