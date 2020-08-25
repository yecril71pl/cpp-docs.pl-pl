---
title: Concurrency::direct3d, funkcje przestrzeni nazw (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: bf98249001c2b8227581fbbbcceeebd085e5d820
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831115"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d, funkcje przestrzeni nazw (AMP)

:::row:::
   :::column span="":::
      [ABS](#abs)\
      [opraw](#clamp)\
      [countbits —](#countbits)\
      [create_accelerator_view](#create_accelerator_view)\
      [d3d_access_lock](#d3d_access_lock)\
      [d3d_access_try_lock](#d3d_access_try_lock)\
      [d3d_access_unlock](#d3d_access_unlock)
   :::column-end:::
   :::column span="":::
      [firstbithigh —](#firstbithigh)\
      [firstbitlow —](#firstbitlow)\
      [get_buffer](#get_buffer)\
      [get_device](#get_device)\
      [imax](#imax)\
      [imin](#imin)\
      [is_timeout_disabled](#is_timeout_disabled)
   :::column-end:::
   :::column span="":::
      [Mad —](#mad)\
      [make_array](#make_array)\
      [emitowan](#noise)\
      [radianach](#radians)\
      [Analiza](#rcp)\
      [reversebits —](#reversebits)
   :::column-end:::
   :::column span="":::
      [Saturate —](#saturate)\
      [zapis](#sign)\
      [smoothstep —](#smoothstep)\
      [czynności](#step)\
      [UMAX](#umax)\
      [umin](#umin)
   :::column-end:::
:::row-end:::

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h **przestrzeń nazw:** współbieżność

## <a name="abs"></a><a name="abs"></a> ABS

Zwraca wartość bezwzględną argumentu.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu.

## <a name="clamp"></a><a name="clamp"></a> opraw

Oblicza wartość pierwszego określonego argumentu, który jest zamocowany do zakresu zdefiniowanego przez drugi i trzeci określony argument.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość, która ma zostać zamocowana

*_Min*<br/>
Dolna granica zakresu ograniczania.

*_Max*<br/>
Górna granica zakresu ograniczania.

### <a name="return-value"></a>Wartość zwracana

Zamocowana wartość `_X` .

## <a name="countbits"></a><a name="countbits"></a> countbits —

Zlicza liczbę bitów zestawu w _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość liczby całkowitej bez znaku

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bitów zestawu w _X

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a> create_accelerator_view

Tworzy obiekt [accelerator_view](accelerator-view-class.md) ze wskaźnika do interfejsu urządzenia Direct3D.

## <a name="syntax"></a>Składnia

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*_Accelerator*<br/>
Akcelerator, dla którego ma zostać utworzony nowy accelerator_view.

*_D3D_device*<br/>
Wskaźnik do interfejsu urządzenia Direct3D.

*_Disable_timeout*<br/>
Parametr logiczny określający, czy należy wyłączyć limit czasu dla nowo utworzonego accelerator_view. Odnosi się to do flagi D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT dla tworzenia urządzenia Direct3D i służy do wskazywania, czy system operacyjny powinien zezwalać na obciążenia, które trwają więcej niż 2 sekundy, bez resetowania urządzenia zgodnie z mechanizmem wykrywania i odzyskiwania limitu czasu systemu Windows. Użycie tej flagi jest zalecane, jeśli trzeba wykonać czasochłonne zadania na accelerator_view.

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) , który ma zostać użyty dla nowo utworzonego accelerator_view. Ten parametr ma wartość domyślną `queuing_mode_automatic` .

## <a name="return-value"></a>Wartość zwracana

`accelerator_view`Obiekt utworzony z porzuconego interfejsu urządzenia Direct3D.

## <a name="remarks"></a>Uwagi

Ta funkcja tworzy nowy `accelerator_view` obiekt na podstawie istniejącego wskaźnika do interfejsu urządzenia Direct3D. Jeśli wywołanie funkcji powiedzie się, liczba odwołań parametru jest zwiększana za pomocą `AddRef` wywołania do interfejsu. Możesz bezpiecznie zwolnić obiekt, gdy nie jest już wymagany w kodzie DirectX. Jeśli wywołanie metody nie powiedzie się, zostanie zgłoszony [runtime_exception](runtime-exception-class.md) .

`accelerator_view`Obiekt tworzony za pomocą tej funkcji jest bezpieczny wątkowo. Należy zsynchronizować współbieżne użycie `accelerator_view` obiektu. Niezsynchronizowane współbieżne użycie `accelerator_view` obiektu i interfejsu RAW ID3D11Device powoduje niezdefiniowane zachowanie.

Środowisko uruchomieniowe C++ AMP zapewnia szczegółowe informacje o błędzie w trybie debugowania, używając warstwy debugowania D3D, jeśli używasz `D3D11_CREATE_DEVICE_DEBUG` flagi.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a> d3d_access_lock

Uzyskaj blokadę na accelerator_view w celu bezpiecznego wykonywania operacji D3D na zasobach współużytkowanych z accelerator_view. Accelerator_view i wszystkie zasoby C++ AMP skojarzone z tym accelerator_view wewnętrznie przejęcia tej blokady podczas wykonywania operacji i blokują, podczas gdy inny wątek utrzymuje blokadę dostępu D3D. Ta blokada nie jest cykliczna: jest to niezdefiniowane zachowanie do wywołania tej funkcji z wątku, w którym już zablokowano blokadę. Jest to niezdefiniowane zachowanie do wykonywania operacji na accelerator_view lub dowolnego kontenera danych skojarzonego z accelerator_view z wątku, który posiada blokadę dostępu D3D. Zobacz również scoped_d3d_access_lock, klasy RAII dla blokady dostępu D3D opartej na zakresie.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view do zablokowania.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a> d3d_access_try_lock

Spróbuj uzyskać blokadę dostępu D3D na accelerator_view bez blokowania.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view do zablokowania.

### <a name="return-value"></a>Wartość zwracana

ma wartość true, jeśli Blokada została pobrana lub ma wartość FAŁSZ, jeśli jest aktualnie utrzymywana przez inny wątek.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a> d3d_access_unlock

Zwolnij blokadę dostępu D3D dla danego accelerator_view. Jeśli wątek wywołujący nie utrzymuje blokady na accelerator_view wyniki są niezdefiniowane.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view, dla którego ma zostać wydana blokada.

## <a name="firstbithigh"></a><a name="firstbithigh"></a> firstbithigh —

Pobiera lokalizację pierwszego zestawu bit w _X, rozpoczynając od najwyższego poziomu i przesuwając go do najniższego bitu kolejności.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Lokalizacja pierwszego zestawu

## <a name="firstbitlow"></a><a name="firstbitlow"></a> firstbitlow —

Pobiera lokalizację pierwszego zestawu bit w _X, rozpoczynając od najniższej kolejności i działającej w kierunku bitu najwyższego rzędu.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca lokalizację pierwszego zestawu.

## <a name="get_buffer"></a><a name="get_buffer"></a> get_buffer

Pobierz interfejs buforu Direct3D określony przez określoną tablicę.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów w tablicy.

*_Rank*<br/>
Ranga tablicy.

*_Array*<br/>
Tablica na accelerator_view Direct3D, dla którego zwracany jest interfejs podstawowego buforu Direct3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający buforowi Direct3D źródłowej tablicy.

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

Pobierz interfejs urządzenia D3D jako accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*AV*<br/>
Accelerator_view D3D, dla którego zwracany jest podstawowy interfejs urządzenia D3D.

### <a name="return-value"></a>Wartość zwracana

`IUnknown`Wskaźnik interfejsu urządzenia D3D, na którym znajduje się accelerator_view.

## <a name="imax"></a><a name="imax"></a> imax

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="imin"></a><a name="imin"></a> imin

Określ minimalną wartość liczbową argumentów

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwróć minimalną wartość liczbową argumentów

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a> is_timeout_disabled

Zwraca flagę logiczną wskazującą, czy limit czasu jest wyłączony dla określonego accelerator_view. Odnosi się do flagi D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT dla tworzenia urządzenia Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, dla którego ustawienie limitu czasu wyłączone ma być zapytania.

### <a name="return-value"></a>Wartość zwracana

Flaga logiczna wskazująca, czy limit czasu jest wyłączony dla określonego accelerator_view.

## <a name="mad"></a><a name="mad"></a> Mad —

Oblicza iloczyn pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy określony argument.

*_Y*<br/>
Drugi określony argument.

*_Z*<br/>
Trzeci określony argument.

### <a name="return-value"></a>Wartość zwracana

Wynik `_X` \* `_Y`  +  `_Z` .

## <a name="make_array"></a><a name="make_array"></a> make_array

Utwórz tablicę ze wskaźnika interfejsu buforu Direct3D.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementu tablicy, który ma zostać utworzony.

*_Rank*<br/>
Ranga tablicy, która ma zostać utworzona.

*_Extent*<br/>
Zakres, który opisuje kształt zagregowanej tablicy.

*_Rv*<br/>
Widok akceleratora D3D, na którym ma zostać utworzona tablica.

*_D3D_buffer*<br/>
Wskaźnik interfejsu IUnknown buforu D3D, z którego ma zostać utworzona tablica.

### <a name="return-value"></a>Wartość zwracana

Tablica utworzona przy użyciu dostarczonego buforu Direct3D.

## <a name="noise"></a><a name="noise"></a> emitowan

Generuje losową wartość przy użyciu algorytmu szum w języku Perl

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, z której ma zostać wygenerowany szum w języku Perl

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość szumu w języku perl z zakresu od-1 do 1.

## <a name="radians"></a><a name="radians"></a> radianach

Konwertuje _X z stopni na radiany

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X przekonwertowany z stopni na radiany

## <a name="rcp"></a><a name="rcp"></a> Analiza

Oblicza odwrotność określonego argumentu przy użyciu szybkiego przybliżenia.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość, dla której ma zostać obliczona odwrotność.

### <a name="return-value"></a>Wartość zwracana

Odwrotność określonego argumentu.

## <a name="reversebits"></a><a name="reversebits"></a> reversebits —

Odwraca kolejność bitów w _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość liczby całkowitej bez znaku

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość z kolejnością bitową odwróconą w _X

## <a name="saturate"></a><a name="saturate"></a> Saturate —

Powoduje, że _X w zakresie od 0 do 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X zamocowany w zakresie od 0 do 1

## <a name="sign"></a><a name="sign"></a> zapis

Określa znak określonego argumentu.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Znak argumentu.

## <a name="smoothstep"></a><a name="smoothstep"></a> smoothstep —

Zwraca gładką interpolację Hermite z zakresu od 0 do 1, jeśli _X należy do zakresu [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Min*<br/>
Wartość zmiennoprzecinkowa

*_Max*<br/>
Wartość zmiennoprzecinkowa

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli _X jest mniejsza niż _Min; 1 Jeśli _X jest większa niż _Max; w przeciwnym razie wartość z zakresu od 0 do 1, jeśli _X należy do zakresu [_Min, _Max]

## <a name="step"></a><a name="step"></a> czynności

Porównuje dwie wartości, zwracając wartość 0 lub 1 na podstawie wartości większej

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Wartość zmiennoprzecinkowa

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość 1, jeśli _X jest większa lub równa _Y; w przeciwnym razie 0

## <a name="umax"></a><a name="umax"></a> UMAX

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="umin"></a><a name="umin"></a> umin

Określ minimalną wartość liczbową argumentów

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwróć minimalną wartość liczbową argumentów

## <a name="see-also"></a>Zobacz też

[Concurrency::direct3d — Przestrzeń nazw](concurrency-direct3d-namespace.md)
