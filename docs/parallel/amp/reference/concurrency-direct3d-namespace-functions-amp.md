---
title: CONCURRENCY::Direct3D funkcje przestrzeni nazw (AMP)
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
ms.openlocfilehash: 0a2977faf094aafb6290063e39e062ffaeaaec81
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281339"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>CONCURRENCY::Direct3D funkcje przestrzeni nazw (AMP)

||||
|-|-|-|
|[abs](#abs)|[clamp](#clamp)|[countbits —](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh —](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad —](#mad)|[make_array](#make_array)|[noise](#noise)|
|[wartość w radianach](#radians)|[rcp](#rcp)|[reversebits —](#reversebits)|
|[Saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[step](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h **Namespace:** Współbieżność

##  <a name="abs"></a>  ABS

Zwraca wartość bezwzględną argumentu

```
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu.

##  <a name="clamp"></a>  Ograniczenie

Oblicza wartość pierwszego określonego argumentu przytwierdzoną do zakresu zdefiniowanego przez drugi i trzeci określony argument.

```
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
Wartość do powiązania

*_Min*<br/>
Granica dolna granica zakresu ustalania poziomu.

*_Max*<br/>
Górna granica granica zakresu ustalania poziomu.

### <a name="return-value"></a>Wartość zwracana

Wartość z przedziału `_X`.

##  <a name="countbits"></a>  countbits —

Zlicza liczbę bitów zestawu w _X

```
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość liczby całkowitej bez znaku

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bitów zestawu w _X

## <a name="create_accelerator_view"></a> create_accelerator_view —

Tworzy [accelerator_view](accelerator-view-class.md) obiekt ze wskaźnika do interfejsu urządzenia Direct3D.

## <a name="syntax"></a>Składnia

```
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

#### <a name="parameters"></a>Parametry

*_Accelerator*<br/>
Akcelerator, na którym ma być tworzony nowy accelerator_view.

*_D3D_device*<br/>
Wskaźnik do interfejsu urządzenia Direct3D.

*_Disable_timeout*<br/>
Parametr logiczny, który określa, czy limit czasu powinien być wyłączony dla nowo utworzonego accelerator_view. To odnosi się do d3d11_create_device_disable_gpu_timeout dla tworzenia urządzenia Direct3D i służy do wskazywania, jeśli system operacyjny powinien zezwalać na obciążenia, które mają więcej niż 2 sekundy, aby wykonać bez resetowania urządzenie na limit czasu Windows mechanizm wykrywania i odzyskiwania. Jeśli zachodzi potrzeba wykonania czasochłonnych zadań na accelerator_view, zalecane jest użycie tej flagi.

*_Qmode*<br/>
[Queuing_mode —](concurrency-namespace-enums-amp.md#queuing_mode) służący do nowo utworzonego accelerator_view. Ten parametr ma wartość domyślną `queuing_mode_automatic`.

## <a name="return-value"></a>Wartość zwracana

`accelerator_view` Obiektu utworzonego na podstawie przekazanego interfejsu urządzenia Direct3D.

## <a name="remarks"></a>Uwagi

Ta funkcja tworzy nową `accelerator_view` obiekt z istniejącego wskaźnika do interfejsu urządzenia Direct3D. Jeśli wywołanie funkcji się powiedzie, licznik odwołań parametru jest zwiększany przez `AddRef` wywołań do interfejsu. Obiekt może zwolnić bezpiecznie, gdy nie jest już wymagany w kodzie programu DirectX. W przypadku niepowodzenia wywołania metody [runtime_exception](runtime-exception-class.md) zgłaszany.

`accelerator_view` Obiekt, który można utworzyć za pomocą tej funkcji jest bezpieczny dla wątków. Należy zsynchronizować współbieżne używanie obiektu `accelerator_view` obiektu. Niezsynchronizowane współbieżne używanie obiektu `accelerator_view` obiektu i surowego interfejsu ID3D11Device powoduje niezdefiniowane zachowanie.

Środowisko wykonawcze C++ AMP zawiera szczegółowe informacje o błędzie w trybie debugowania przy użyciu warstwy D3D debugowania, jeśli używasz `D3D11_CREATE_DEVICE_DEBUG` flagi.

##  <a name="d3d_access_lock"></a>  d3d_access_lock —

Uzyskaj blokadę na accelerator_view w celu bezpiecznego wykonywania operacji D3D na zasobach współużytkowanych wraz z accelerator_view. Obiekt accelerator_view i wszystkie zasoby C++ AMP skojarzone z tym obiektem accelerator_view wewnętrznie nakładają tę blokadę podczas wykonywania operacji i są blokowane, gdy inny wątek nałoży blokadę dostępu D3D. Ta blokada nie jest cykliczna: Jest to niezdefiniowane zachowanie, aby wywołać tę funkcję z wątku, który już posiada blokadę. To zachowanie niezdefiniowane do wykonywania operacji na widoku akcelatora lub dowolnego kontenera danych skojarzonych z widokiem akcelatora z wątku, który posiada blokadę dostępu D3D. Zobacz też: scoped_d3d_access_lock, klasa stylu RAII na blokadę dostępu D3D zakresu.

```
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Obiekt accelerator_view do zablokowania.

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock

Próba uzyskania blokady dostępu D3D na accelerator_view bez blokowania.

```
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Obiekt accelerator_view do zablokowania.

### <a name="return-value"></a>Wartość zwracana

wartość true, jeśli blokada została uzyskana lub false, jeśli jest aktualnie trzymana przez inny wątek.

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock

Zwolnij blokadę dostępu D3D danego widoku akceleratora. Jeśli wątek wywołujący nie posiada blokadę na accelerator_view wyniki są niezdefiniowane.

```
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Obiekt accelerator_view, dla którego blokada ma zostać zwolniona.

##  <a name="firstbithigh"></a>  firstbithigh —

Pobiera lokalizację pierwszego ustawionego bitu _X, zaczynając od bitu najwyższego rzędu i kierunku bitu o najniższej kolejności.

```
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Lokalizacja pierwszego ustawionego bitu

##  <a name="firstbitlow"></a>  firstbitlow —

Pobiera lokalizację pierwszego ustawionego bitu _X, zaczynając od bitu najniższego rzędu i pracy w kierunku bitu o najwyższej kolejności.

```
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca lokalizację pierwszego ustawionego bitu.

##  <a name="get_buffer"></a>  get_buffer —

Pobieranie interfejsu buforu Direct3D podstaw określonej tablicy.

```
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
Zwracany jest tablica obiektu Direct3D accelerator_view, dla którego interfejs odpowiadającego buforu Direct3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający buforowi Direct3D tablicy.

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device

Uzyskaj podstawowe accelerator_view interfejsu urządzenia D3D.

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*Pliki audio i wideo*<br/>
Widok akceleratora D3D, dla którego jest zwracany podstawowego interfejsu urządzenia D3D.

### <a name="return-value"></a>Wartość zwracana

`IUnknown` Wskaźnika interfejsu bazowego accelerator_view urządzenia D3D.

##  <a name="imax"></a>  Imax

Określić maksymalną wartość liczbową z podanych argumentów

```
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

Zwraca największą wartość liczbową z podanych argumentów

##  <a name="imin"></a>  imin —

Określić minimalną wartość liczbową z podanych argumentów

```
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

Zwraca minimalną wartość liczbową argumentów

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled —

Zwraca flagę logiczną wskazującą, czy limit czasu jest wyłączony dla określonego obiektu accelerator_view. Odpowiada to d3d11_create_device_disable_gpu_timeout dla tworzenia urządzenia Direct3D.

```
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, dla którego wyłączonego ustawienia limitu czasu ma zostać wykonane zapytanie.

### <a name="return-value"></a>Wartość zwracana

Flaga logiczna wskazująca, czy limit czasu jest wyłączony dla określonego obiektu accelerator_view.

##  <a name="mad"></a>  mad —

Oblicza produkt pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument.

```
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

Wynik `_X` \* `_Y`  +  `_Z`.

##  <a name="make_array"></a>  make_array —

Utwórz tablicę ze wskaźnika interfejsu buforu Direct3D.

```
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
Ranga tablicy, który ma zostać utworzony.

*_Extent*<br/>
Zakres opisujący kształt agregacji tablicy.

*_Rv*<br/>
Widok akceleratora D3D, na którym ma zostać utworzony tablicy.

*_D3D_buffer*<br/>
Wskaźnik interfejsu IUnknown buforu D3D, aby utworzyć tablicę z.

### <a name="return-value"></a>Wartość zwracana

Tablica utworzona przy użyciu dostarczonego buforu Direct3D.

##  <a name="noise"></a>  szumów

Generuje losową wartość przy użyciu algorytmu szumu Perlin

```
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, z której ma zostać wygenerowana szumu Perlin

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość szumu Perlin w zakresie od -1 do 1

##  <a name="radians"></a>  wartość w radianach

Konwertuje _X ze stopni na radiany

```
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X skonwertowaniu stopnie na radiany

##  <a name="rcp"></a>  rcp

Oblicza odwrotność określonego argumentu za pomocą szybkiego zbliżenia.

```
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość, dla którego ma zostać należy wyliczyć odwrotność.

### <a name="return-value"></a>Wartość zwracana

Odwrotność określonego argumentu.

##  <a name="reversebits"></a>  reversebits —

Odwraca kolejność bitów w _X

```
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość liczby całkowitej bez znaku

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość o kolejność bitów wycofana w _X

##  <a name="saturate"></a>  Saturate

Ogranicza _X do zakresu od 0 do 1

```
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X powiązany do zakresu od 0 do 1

##  <a name="sign"></a>  Logowanie

Określa znak określonego argumentu.

```
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Znak argumentu.

##  <a name="smoothstep"></a>  smoothstep —

Zwraca smooth gładką interpolację wielomianu hermite'a pomiędzy 0 a 1, jeśli _X jest w zakresie [_Min, _Max].

```
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

Zwraca wartość 0, jeśli _X jest mniejsza niż _Min; 1, jeśli _X jest większa niż _Max; w przeciwnym razie wartość z zakresu od 0 do 1, jeśli _X jest w zakresie [_Min, _Max]

##  <a name="step"></a>  Krok

Porównuje dwie wartości, zwracając 0 lub 1, w oparciu o wartość, która jest większa

```
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

Zwraca wartość 1, jeśli _X jest większa niż lub równa _Y; w przeciwnym razie 0.

##  <a name="umax"></a>  UMAX

Określić maksymalną wartość liczbową z podanych argumentów

```
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

Zwraca największą wartość liczbową z podanych argumentów

##  <a name="umin"></a>  umin —

Określić minimalną wartość liczbową z podanych argumentów

```
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

Zwraca minimalną wartość liczbową argumentów

## <a name="see-also"></a>Zobacz także

[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)
