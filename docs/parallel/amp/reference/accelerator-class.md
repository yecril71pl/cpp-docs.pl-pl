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
ms.openlocfilehash: 99747899e9264404244d66f3f0d18bee5d2b0967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182710"
---
# <a name="accelerator-class"></a>accelerator — Klasa

Akcelerator jest funkcją sprzętową zoptymalizowaną pod kątem przetwarzania danych równoległych. Akcelerator może być urządzeniem podłączonym do magistrali PCIe (na przykład GPU) lub może być rozszerzoną instrukcją ustawioną na głównym procesorze CPU.

## <a name="syntax"></a>Składnia

```cpp
class accelerator;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor akceleratora](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator`.|
|[~ Accelerator — destruktor](#ctor)|Niszczy `accelerator` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[create_view](#create_view)|Tworzy i zwraca `accelerator_view` obiekt dla tego akceleratora.|
|[get_all](#get_all)|Zwraca wektor `accelerator` obiektów, które reprezentują wszystkie dostępne akceleratory.|
|[get_auto_selection_view](#get_auto_selection_view)|Zwraca wybór autowybierany `accelerator_view` .|
|[get_dedicated_memory](#get_dedicated_memory)|Zwraca dedykowaną pamięć dla `accelerator` , w kilobajtach.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Zwraca domyślną [access_type](concurrency-namespace-enums-amp.md#access_type) dla buforów utworzonych w tym akceleratorze.|
|[get_default_view](#get_default_view)|Zwraca domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator` .|
|[get_description](#get_description)|Zwraca Krótki opis `accelerator` urządzenia.|
|[get_device_path](#get_device_path)|Zwraca ścieżkę urządzenia.|
|[get_has_display](#get_has_display)|Określa, czy `accelerator` jest dołączony do wyświetlania.|
|[get_is_debug](#get_is_debug)|Określa, czy `accelerator` ma włączoną WARSTWĘ debugowania dla obszernego raportowania błędów.|
|[get_is_emulated](#get_is_emulated)|Określa, czy `accelerator` jest emulowany.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Określa, czy `accelerator` obsługuje pamięć współużytkowaną|
|[get_supports_double_precision](#get_supports_double_precision)|Określa, czy `accelerator` jest dołączony do wyświetlania.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Określa, czy `accelerator` ma ograniczoną obsługę obliczeń matematycznych podwójnej precyzji.|
|[get_version](#get_version)|Zwraca wersję programu `accelerator` .|
|[set_default](#set_default)|Zwraca ścieżkę domyślnego akceleratora.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Ustawia domyślny [ACCESS_TYPE](concurrency-namespace-enums-amp.md#access_type)procesora dla tablic i niejawnych alokacji pamięci wykonanych na tym komputerze `accelerator` .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator! =](#operator_neq)|Porównuje ten `accelerator` obiekt z innym i zwraca **`false`** , jeśli są takie same; w przeciwnym razie zwraca **`true`** .|
|[operator =](#operator_eq)|Kopiuje zawartość określonego `accelerator` obiektu do tego elementu.|
|[operator = =](#operator_eq_eq)|Porównuje ten `accelerator` obiekt z innym i zwraca **`true`** , jeśli są takie same; w przeciwnym razie zwraca **`false`** .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Pobiera stałą typu String dla procesora CPU `accelerator` .|
|[dedicated_memory](#dedicated_memory)|Pobiera dedykowaną pamięć dla `accelerator` , w kilobajtach.|
|[default_accelerator](#default_accelerator)|Pobiera stałą typu String dla ustawienia domyślnego `accelerator` .|
|[default_cpu_access_type](#default_cpu_access_type)|Pobiera lub ustawia domyślny [ACCESS_TYPE](concurrency-namespace-enums-amp.md#access_type)procesora dla tablic i niejawnych alokacji pamięci wykonanych na tym komputerze `accelerator` .|
|[default_view](#default_view)|Pobiera domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator` .|
|[zharmonizowan](#description)|Pobiera Krótki opis `accelerator` urządzenia.|
|[device_path](#device_path)|Pobiera ścieżkę urządzenia.|
|[direct3d_ref](#direct3d_ref)|Pobiera stałą typu String dla odwołania Direct3D `accelerator` .|
|[direct3d_warp](#direct3d_warp)|Pobiera stałą typu String dla `accelerator` obiektu, którego można użyć do wykonywania kodu C++ amp na wielordzeniowych procesorach, które używają Streaming SIMD Extensions (SSE).|
|[has_display](#has_display)|Pobiera wartość logiczną wskazującą, czy `accelerator` jest dołączona do wyświetlania.|
|[is_debug](#is_debug)|Wskazuje, czy `accelerator` ma włączoną WARSTWĘ debugowania dla obszernego raportowania błędów.|
|[is_emulated](#is_emulated)|Wskazuje, czy `accelerator` jest emulowany.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Wskazuje, czy `accelerator` obsługuje pamięć współużytkowaną.|
|[supports_double_precision](#supports_double_precision)|Wskazuje, czy akcelerator obsługuje matematykę o podwójnej precyzji.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Wskazuje, czy akcelerator ma ograniczoną obsługę obliczeń matematycznych podwójnej precyzji.|
|[Wersja](#version)|Pobiera wersję programu `accelerator` .|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`accelerator`

## <a name="remarks"></a>Uwagi

Akcelerator jest funkcją sprzętową zoptymalizowaną pod kątem przetwarzania danych równoległych. Akcelerator jest często dyskretnym procesorem GPU, ale może być także wirtualną jednostką po stronie hosta, taką jak urządzenie DirectX REF, Wypaczenie (urządzenie po stronie procesora, które jest przyspieszone przy użyciu instrukcji SSE) lub samego procesora.

Można skonstruować `accelerator` obiekt przez Wyliczenie dostępnego urządzenia lub przez pobranie urządzenia domyślnego, urządzenia odniesienia lub urządzenia WYpaczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności

## <a name="a-accelerator"></a><a name="dtor"></a></a>Akcelerator ~

Niszczy `accelerator` obiekt.

```cpp
~accelerator();
```

### <a name="return-value"></a>Wartość zwracana

## <a name="accelerator"></a><a name="ctor"></a>skrót

Inicjuje nowe wystąpienie [klasy akceleratora](accelerator-class.md).

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Device_path*<br/>
Ścieżka urządzenia fizycznego.

*_Other*<br/>
Akcelerator do skopiowania.

## <a name="cpu_accelerator"></a><a name="cpu_accelerator"></a>cpu_accelerator

Pobiera stałą typu String dla akceleratora procesora.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a><a name="create_view"></a>create_view

Tworzy i zwraca `accelerator_view` obiekt na tym akceleratorze przy użyciu określonego trybu kolejkowania. Gdy nie określono trybu kolejkowania, nowy program `accelerator_view` używa trybu kolejkowania [queuing_mode:: natychmiastowe](concurrency-namespace-enums-amp.md#queuing_mode) .

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*qmode*<br/>
Tryb kolejkowania.

### <a name="return-value"></a>Wartość zwracana

Nowy `accelerator_view` obiekt w tym akceleratorze, przy użyciu określonego trybu kolejkowania.

## <a name="dedicated_memory"></a><a name="dedicated_memory"></a>dedicated_memory

Pobiera dedykowaną pamięć dla `accelerator` , w kilobajtach.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a><a name="default_accelerator"></a>default_accelerator

Pobiera stałą typu String dla ustawienia domyślnego `accelerator` .

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a><a name="default_cpu_access_type"></a>default_cpu_access_type

Domyślny [access_type](concurrency-namespace-enums-amp.md#access_type)procesora dla tablic i niejawnych alokacji pamięci wykonanych na tym komputerze `accelerator` .

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a><a name="default_view"></a>default_view

Pobiera domyślny widok akceleratora, który jest skojarzony z `accelerator` .

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a><a name="description"></a>zharmonizowan

Pobiera Krótki opis `accelerator` urządzenia.

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a><a name="device_path"></a>device_path

Pobiera ścieżkę akceleratora. Ścieżka jest unikatowa w systemie.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a><a name="direct3d_ref"></a>direct3d_ref

Pobiera stałą typu String dla akceleratora odwołania Direct3D.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a><a name="direct3d_warp"></a>direct3d_warp

Pobiera stałą typu String dla `accelerator` obiektu, którego można użyć do wykonywania kodu C++ amp na wielordzeniowych procesorach przy użyciu funkcji Streaming SIMD Extensions (SSE).

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a><a name="get_all"></a>get_all

Zwraca wektor `accelerator` obiektów, które reprezentują wszystkie dostępne akceleratory.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Wartość zwracana

Wektor dostępnych akceleratorów

## <a name="get_auto_selection_view"></a><a name="get_auto_selection_view"></a>get_auto_selection_view

Zwraca automatyczny wybór accelerator_view, który po określeniu jako docelowy parallel_for_each powoduje, że element docelowy accelerator_view do wykonania jądra parallel_for_each zostanie automatycznie wybrany przez środowisko uruchomieniowe. We wszystkich innych celach accelerator_view zwracany przez tę metodę jest taka sama jak domyślna accelerator_view akceleratora domyślnego

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Wartość zwracana

Wybór autowybierany accelerator_view.

## <a name="get_dedicated_memory"></a><a name="get_dedicated_memory"></a>get_dedicated_memory

Zwraca dedykowaną pamięć dla `accelerator` , w kilobajtach.

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Wartość zwracana

Dedykowana pamięć dla `accelerator` , w kilobajtach.

## <a name="get_default_cpu_access_type"></a><a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

Pobiera domyślny access_type procesora dla buforów utworzonych w tym akceleratorze

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślna access_type procesora dla buforów utworzonych w tym akceleratorze.

## <a name="get_default_view"></a><a name="get_default_view"></a>get_default_view

Zwraca domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator` .

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny `accelerator_view` obiekt, który jest skojarzony z `accelerator` .

## <a name="get_description"></a><a name="get_description"></a>get_description

Zwraca Krótki opis `accelerator` urządzenia.

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>Wartość zwracana

Krótki opis `accelerator` urządzenia.

## <a name="get_device_path"></a><a name="get_device_path"></a>get_device_path

Zwraca ścieżkę akceleratora. Ścieżka jest unikatowa w systemie.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowa ścieżka wystąpienia urządzenia dla całego systemu.

## <a name="get_has_display"></a><a name="get_has_display"></a>get_has_display

Zwraca wartość logiczną wskazującą, czy `accelerator` można wyprowadzać dane wyjściowe do wyświetlania.

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `accelerator` dane mogą wynikać z wyświetlania; w przeciwnym razie **`false`** .

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Określa, czy `accelerator` ma włączoną WARSTWĘ debugowania dla obszernego raportowania błędów.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `accelerator` ma włączoną WARSTWĘ debugowania dla obszernego raportowania błędów. W przeciwnym razie **`false`** .

## <a name="get_is_emulated"></a><a name="get_is_emulated"></a>get_is_emulated

Określa, czy `accelerator` jest emulowany.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `accelerator` jest emulowany. W przeciwnym razie **`false`** .

## <a name="get_supports_cpu_shared_memory"></a><a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

Zwraca wartość logiczną wskazującą, czy akcelerator obsługuje pamięć dostępną zarówno dla akceleratora, jak i procesora.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli akcelerator obsługuje pamięć współużytkowaną procesora CPU; w przeciwnym razie **`false`** .

## <a name="get_supports_double_precision"></a><a name="get_supports_double_precision"></a>get_supports_double_precision

Zwraca wartość logiczną wskazującą, czy akcelerator obsługuje matematykę o podwójnej precyzji, w tym odmowa dodawania, dzielenia, wzajemności i rzutowania między **`int`** i**`double`**

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli akcelerator obsługuje matematykę o podwójnej precyzji; w przeciwnym razie **`false`** .

## <a name="get_supports_limited_double_precision"></a><a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

Zwraca wartość logiczną wskazującą, czy akcelerator ma ograniczoną obsługę matematycznej podwójnej precyzji. Jeśli akcelerator ma tylko ograniczoną pomoc techniczną, należy odmówić, że **`int`** **`double`** jest to nieobsługiwane.

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli akcelerator ma ograniczoną obsługę matematycznej podwójnej precyzji; w przeciwnym razie **`false`** .

## <a name="get_version"></a><a name="get_version"></a>get_version

Zwraca wersję programu `accelerator` .

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja programu `accelerator` .

## <a name="has_display"></a><a name="has_display"></a>has_display

Pobiera wartość logiczną wskazującą, czy `accelerator` można wyprowadzać dane wyjściowe do wyświetlania.

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Pobiera wartość logiczną wskazującą, czy `accelerator` ma włączoną WARSTWĘ debugowania dla obszernego raportowania błędów.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a><a name="is_emulated"></a>is_emulated

Pobiera wartość logiczną wskazującą, czy `accelerator` jest emulowany.

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator"></a><a name="operator_neq"></a>operator! =

Porównuje ten `accelerator` obiekt z innym i zwraca **`false`** , jeśli są takie same; w przeciwnym razie zwraca **`true`** .

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`accelerator`Obiekt, który ma zostać porównany z tym elementem.

### <a name="return-value"></a>Wartość zwracana

**`false`** Jeśli dwa `accelerator` obiekty są takie same; w przeciwnym razie **`true`** .

## <a name="operator"></a><a name="operator_eq"></a>operator =

Kopiuje zawartość określonego `accelerator` obiektu do tego elementu.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`accelerator`Obiekt, z którego mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `accelerator` obiektu.

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

Porównuje ten `accelerator` obiekt z innym i zwraca **`true`** , jeśli są takie same; w przeciwnym razie zwraca **`false`** .

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`accelerator`Obiekt, który ma zostać porównany z tym elementem.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli inny `accelerator` obiekt jest taki sam jak ten `accelerator` obiekt; w przeciwnym razie, **`false`** .

## <a name="set_default"></a><a name="set_default"></a>set_default

Ustawia akcelerator domyślny, który ma być używany dla każdej operacji, która niejawnie używa akceleratora domyślnego. Ta metoda kończy się powodzeniem tylko wtedy, gdy wybrany akcelerator domyślny środowiska uruchomieniowego nie został jeszcze użyty w operacji, która niejawnie używa akceleratora domyślnego

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parametry

*_Path*<br/>
Ścieżka do akceleratora.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wywołanie powiedzie się po ustawieniu akceleratora domyślnego. W przeciwnym razie **`false`** .

## <a name="set_default_cpu_access_type"></a><a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

Ustaw domyślne access_type procesora dla tablic utworzonych w tym akceleratorze lub dla niejawnych alokacji pamięci w ramach array_views dostępnym dla tego akceleratora. Ta metoda kończy się powodzeniem tylko wtedy, gdy default_cpu_access_type dla akceleratora nie została jeszcze zastąpiona przez poprzednie wywołanie tej metody, a środowisko uruchomieniowe wybrane default_cpu_access_type dla tego akceleratora nie zostało jeszcze użyte do przydzielenia tablicy lub niejawnego przydziału pamięci w celu utworzenia array_view dostępnym dla tego akceleratora.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parametry

*_Default_cpu_access_type*<br/>
Domyślny access_type procesora, który ma być używany na potrzeby alokacji pamięci Array/array_view na tym akceleratorze.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna wskazująca, czy domyślny access_type procesora dla akceleratora został pomyślnie ustawiony.

## <a name="supports_cpu_shared_memory"></a><a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

Pobiera wartość logiczną wskazującą, czy `accelerator` obsługuje pamięć współużytkowaną.

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a><a name="supports_double_precision"></a>supports_double_precision

Pobiera wartość logiczną wskazującą, czy akcelerator obsługuje matematykę o podwójnej precyzji.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a><a name="supports_limited_double_precision"></a>supports_limited_double_precision

Pobiera wartość logiczną wskazującą, czy akcelerator ma ograniczoną obsługę matematycznej podwójnej precyzji. Jeśli akcelerator ma tylko ograniczoną pomoc techniczną, należy odmówić, że **`int`** **`double`** jest to nieobsługiwane.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>Wersja programu <a name="version"></a>

Pobiera wersję programu `accelerator` .

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
