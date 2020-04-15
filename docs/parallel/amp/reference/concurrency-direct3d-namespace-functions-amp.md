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
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375932"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d, funkcje przestrzeni nazw (AMP)

||||
|-|-|-|
|[Abs](#abs)|[Zacisk](#clamp)|[liczbabitów](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow (pierwszy bitlow)](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[Imax](#imax)|[imin ( imin )](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Mad](#mad)|[make_array](#make_array)|[Hałasu](#noise)|
|[Radianach](#radians)|[Rcp](#rcp)|[odwrócone](#reversebits)|
|[Nasycenia](#saturate)|[Znak](#sign)|[gładki krok](#smoothstep)|
|[krok](#step)|[Umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h **Obszar nazw:** Współbieżność

## <a name="abs"></a><a name="abs"></a>Abs

Zwraca wartość bezwzględną argumentu

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu.

## <a name="clamp"></a><a name="clamp"></a>Zacisk

Oblicza wartość pierwszego określonego argumentu zaciśniętego do zakresu zdefiniowanego przez drugi i trzeci określony argument.

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

*_x*<br/>
Wartość, która ma być zaciśnięta

*_Min*<br/>
Dolna granica zakresu mocowania.

*_Max*<br/>
Górna granica zakresu mocowania.

### <a name="return-value"></a>Wartość zwracana

Zaciśnięte `_X`wartości .

## <a name="countbits"></a><a name="countbits"></a>liczbabitów

Zlicza liczbę ustawionych bitów w _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Niepodpisana wartość całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę ustawionych bitów w _X

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

Tworzy [obiekt accelerator_view](accelerator-view-class.md) ze wskaźnika do interfejsu urządzenia Direct3D.

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
Akcelerator, na którym ma powstać nowy accelerator_view.

*_D3D_device*<br/>
Wskaźnik do interfejsu urządzenia Direct3D.

*_Disable_timeout*<br/>
Parametr logiczny określający, czy limit czasu powinien zostać wyłączony dla nowo utworzonego accelerator_view. Odpowiada to flagi D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT do tworzenia urządzeń Direct3D i służy do wskazania, czy system operacyjny powinien zezwalać na wykonywanie obciążeń, które zajmują więcej niż 2 sekundy bez resetowania urządzenia za pomocą mechanizmu wykrywania i odzyskiwania limitu czasu systemu Windows. Użycie tej flagi jest zalecane, jeśli trzeba wykonać czasochłonne zadania na accelerator_view.

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) do wykorzystania w nowo utworzonych accelerator_view. Ten parametr ma wartość `queuing_mode_automatic`domyślną .

## <a name="return-value"></a>Wartość zwracana

Obiekt `accelerator_view` utworzony na podstawie przekazanego interfejsu urządzenia Direct3D.

## <a name="remarks"></a>Uwagi

Ta funkcja tworzy `accelerator_view` nowy obiekt z istniejącego wskaźnika do interfejsu urządzenia Direct3D. Jeśli wywołanie funkcji powiedzie się, liczba odwołań parametru jest `AddRef` zwiększana za pomocą wywołania interfejsu. Obiekt można bezpiecznie zwolnić, gdy nie jest już wymagany w kodzie DirectX. Jeśli wywołanie metody zakończy się niepowodzeniem, zostanie rzucony [runtime_exception.](runtime-exception-class.md)

Obiekt, `accelerator_view` który można utworzyć za pomocą tej funkcji jest bezpieczny dla wątków. Należy zsynchronizować równoczesne użycie `accelerator_view` obiektu. Niezsynchronizowane jednoczesne użycie `accelerator_view` obiektu i interfejsu raw ID3D11Device powoduje niezdefiniowane zachowanie.

Środowisko wykonawcze C++ AMP zawiera szczegółowe informacje o błędzie w trybie debugowania przy użyciu warstwy debugowania D3D, jeśli używasz `D3D11_CREATE_DEVICE_DEBUG` flagi.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

Uzyskaj blokadę na accelerator_view w celu bezpiecznego wykonywania operacji D3D na zasobach udostępnionych accelerator_view. accelerator_view i wszystkie zasoby C++ AMP skojarzone z tym accelerator_view wewnętrznie podjąć tę blokadę podczas wykonywania operacji i zablokuje, podczas gdy inny wątek posiada blokadę dostępu D3D. Ta blokada nie jest rekursywne: jest niezdefiniowane zachowanie wywołać tę funkcję z wątku, który już posiada blokadę. Jest to zachowanie niezdefiniowane do wykonywania operacji na accelerator_view lub dowolnego kontenera danych skojarzonych z accelerator_view z wątku, który przechowuje blokadę dostępu D3D. Zobacz też scoped_d3d_access_lock, klasy w stylu RAII dla blokady dostępu D3D opartej na zakresie.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
accelerator_view do zablokowania.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

Spróbuj uzyskać blokadę dostępu D3D na accelerator_view bez blokowania.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
accelerator_view do zablokowania.

### <a name="return-value"></a>Wartość zwracana

true, jeśli blokada została nabyta lub false, jeśli jest obecnie w posiadaniu innego wątku.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

Zwolnij blokadę dostępu D3D na danym accelerator_view. Jeśli wątek wywołujący nie posiada blokady na accelerator_view wyniki są niezdefiniowane.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
accelerator_view, dla którego ma zostać zwolniona blokada.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>firstbithigh

Pobiera lokalizację pierwszego bitu zestawu w _X, począwszy od bitu najwyższego rzędu i przechodząc do bitu najniższego rzędu.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Lokalizacja pierwszego bitu zestawu

## <a name="firstbitlow"></a><a name="firstbitlow"></a>firstbitlow (pierwszy bitlow)

Pobiera lokalizację pierwszego bitu zestawu w _X, począwszy od bitu najniższego rzędu i pracy w kierunku bitu najwyższego rzędu.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca lokalizację pierwszego bitu zestawu

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

Pobierz interfejs buforu Direct3D leżący u podstaw określonej tablicy.

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
Tablica na accelerator_view Direct3D, dla której zwracany jest podstawowy interfejs buforu Direct3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający buforowi Direct3D leżącemu u podstaw tablicy.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

Pobierz interfejs urządzenia D3D leżący u podstaw accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*Av*<br/>
D3D accelerator_view, dla którego jest zwracany podstawowy interfejs urządzenia D3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `IUnknown` interfejsu urządzenia D3D leżącego u podstaw accelerator_view.

## <a name="imax"></a><a name="imax"></a>Imax

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="imin"></a><a name="imin"></a>imin ( imin )

Określanie minimalnej wartości liczbowej argumentów

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca minimalną wartość liczbową argumentów

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

Zwraca flagę logiczną wskazującą, że limit czasu jest wyłączony dla określonego accelerator_view. Odpowiada to flagi D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT do tworzenia urządzeń Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, dla którego ma zostać wyszukiwane ustawienie wyłączenia limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Flaga logiczna wskazująca, czy limit czasu jest wyłączony dla określonego accelerator_view.

## <a name="mad"></a><a name="mad"></a>Mad

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

*_x*<br/>
Pierwszy określony argument.

*_y*<br/>
Drugi określony argument.

*_Z*<br/>
Trzeci określony argument.

### <a name="return-value"></a>Wartość zwracana

`_X` \* `_Y`  + Wynik . `_Z`

## <a name="make_array"></a><a name="make_array"></a>make_array

Tworzenie tablicy na podstawie wskaźnika interfejsu buforu Direct3D.

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
Typ elementu tablicy, która ma zostać utworzona.

*_Rank*<br/>
Ranga tablicy, która ma zostać utworzona.

*_Extent*<br/>
Stopień, który opisuje kształt agregacji tablicy.

*_Rv*<br/>
Widok akceleratora D3D, na którym ma zostać utworzona tablica.

*_D3D_buffer*<br/>
IUnknown wskaźnik interfejsu buforu D3D do utworzenia tablicy z.

### <a name="return-value"></a>Wartość zwracana

Tablica utworzona przy użyciu dostarczonego buforu Direct3D.

## <a name="noise"></a><a name="noise"></a>Hałasu

Generuje wartość losową przy użyciu algorytmu szumu Perlina

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, z której ma generować szum Perlina

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość szumu Perlina w zakresie od -1 do 1

## <a name="radians"></a><a name="radians"></a>Radianach

Konwertuje _X z stopni na radiany

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X konwertowane z stopni na radiany

## <a name="rcp"></a><a name="rcp"></a>Rcp

Oblicza odwrotność określonego argumentu przy użyciu szybkiego przybliżenia.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość, dla której można obliczyć wzajemne.

### <a name="return-value"></a>Wartość zwracana

Wzajemność określonego argumentu.

## <a name="reversebits"></a><a name="reversebits"></a>odwrócone

Odwraca kolejność bitów w _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Niepodpisana wartość całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość z odwróconą kolejnością bitów w _X

## <a name="saturate"></a><a name="saturate"></a>Nasycenia

Zaciski _X w zakresie od 0 do 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X zaciśnięte w zakresie od 0 do 1

## <a name="sign"></a><a name="sign"></a>Znak

Określa znak określonego argumentu.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Znak argumentu.

## <a name="smoothstep"></a><a name="smoothstep"></a>gładki krok

Zwraca płynną interpolację pustelnika z zakresu od 0 do 1, jeśli _X znajduje się w zakresie [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Min*<br/>
Wartość zmiennoprzecinowa

*_Max*<br/>
Wartość zmiennoprzecinowa

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli _X jest mniejsza niż _Min; 1, jeżeli _X jest większa niż _Max; w przeciwnym razie wartość z zakresu od 0 do 1, jeśli _X znajduje się w zakresie [_Min, _Max]

## <a name="step"></a><a name="step"></a>Krok

Porównuje dwie wartości, zwracając 0 lub 1 na podstawie wartości, która jest większa

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_y*<br/>
Wartość zmiennoprzecinowa

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość 1, jeśli _X jest większa lub równa _Y; w przeciwnym razie 0

## <a name="umax"></a><a name="umax"></a>Umax

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="umin"></a><a name="umin"></a>umin

Określanie minimalnej wartości liczbowej argumentów

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca minimalną wartość liczbową argumentów

## <a name="see-also"></a>Zobacz też

[Concurrency::direct3d — Przestrzeń nazw](concurrency-direct3d-namespace.md)
