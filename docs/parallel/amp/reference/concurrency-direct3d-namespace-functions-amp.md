---
title: CONCURRENCY::Direct3D — przestrzeń nazw funkcji (AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
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
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b200ce8329c10fe2257ca3ce9ca8cb61125390fc
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>CONCURRENCY::Direct3D — przestrzeń nazw funkcji (AMP)
||||  
|-|-|-|  
|[abs](#abs)|[ograniczenie](#clamp)|[countbits —](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh](#firstbithigh)|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[mad —](#mad)|[make_array](#make_array)|[hałasu](#noise)|  
|[radians](#radians)|[rcp](#rcp)|[reversebits —](#reversebits)|  
|[saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|  
|[step](#step)|[umax](#umax)|[umin](#umin)|  

## <a name="requirements"></a>Wymagania
**Nagłówek:** amp.h **Namespace:** współbieżności
  
##  <a name="abs"></a>  ABS  
 Zwraca wartość bezwzględną argumentu  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość bezwzględną liczby argumentów.  
  
##  <a name="clamp"></a>  ograniczenie  
 Oblicza wartość pierwszy argument określony zablokowane za pomocą do zdefiniowanych przez drugi i trzeci argument określonego zakresu.  
  
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
 `_X`  
 Wartość jest zablokowane, za pomocą  
  
 `_Min`  
 Dolna granica zakresu zaczepów.  
  
 `_Max`  
 Górna granica zakresu zaczepów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość clamped `_X`.  
  
##  <a name="countbits"></a>  countbits —  
 Oblicza liczbę bitów zestawu _X  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
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
 `_Accelerator`  
 Accelerator, na którym ma być tworzony nowy accelerator_view.  
  
 `_D3D_device`  
 Wskaźnik do interfejsu urządzenia Direct3D.  
  
 `_Disable_timeout`  
 Parametr wartość logiczna określająca, czy należy wyłączyć limit czasu, aby nowo utworzony accelerator_view. To odpowiada flagi D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT tworzenia urządzenie Direct3D i służy do wskazywania, czy system operacyjny powinien zezwalać obciążeń, które przyjmują więcej niż 2 sekundy bez zresetowania urządzenia na limit czasu systemu Windows mechanizm wykrywania i odzyskiwania. Jeśli potrzebujesz do wykonywania zadań dużo czasu na accelerator_view, zalecane jest użycie tej flagi.  
  
 `_Qmode`  
 [Queuing_mode —](concurrency-namespace-enums-amp.md#queuing_mode) do zastosowania w przypadku nowo utworzonego accelerator_view. Ten parametr ma wartość domyślną `queuing_mode_automatic`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `accelerator_view` Obiektu utworzone na podstawie przekazany interfejs urządzenie Direct3D.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy nową `accelerator_view` obiektu na podstawie istniejącego wskaźnika do interfejsu urządzenie Direct3D. Jeśli wywołanie funkcji zakończy się powodzeniem, liczba odwołań parametru jest zwiększany za pomocą klasy `AddRef` wywołanie interfejsu. Można bezpiecznie Zwolnij obiektu, gdy nie jest wymagany w kodzie programu DirectX. W przypadku niepowodzenia wywołania metody [runtime_exception —](runtime-exception-class.md) jest generowany.  
  
 `accelerator_view` Obiektu, który utworzono przy użyciu tej funkcji jest bezpieczne dla wątków. Należy przeprowadzić synchronizację współbieżne używanie `accelerator_view` obiektu. Niezsynchronizowane równoczesne użycie `accelerator_view` obiektu i interfejsu pierwotnego ID3D11Device powoduje niezdefiniowane zachowanie.  
  
 Środowiska uruchomieniowego C++ AMP zawiera szczegółowe informacje o błędzie w trybie debugowania przy użyciu warstwy D3D debugowania, jeśli używasz `D3D11_CREATE_DEVICE_DEBUG` flagi.  
  
  
##  <a name="d3d_access_lock"></a>  d3d_access_lock  
 Blokady na accelerator_view na potrzeby bezpiecznego wykonywanie operacji D3D zasobów udostępnionych z accelerator_view. Accelerator_view i wszystkie zasoby C++ AMP skojarzone z tym accelerator_view wewnętrznie potrwać blokady podczas wykonywania operacji i blokuje, podczas gdy inny wątek utrzymuje blokadę dostępu D3D. Ta blokada jest niecykliczne: jest niezdefiniowane zachowanie w wywołaniu tej funkcji z wątku, który już utrzymuje blokadę. Jest niezdefiniowane zachowanie w celu wykonania operacji na accelerator_view lub dowolnego kontenera danych skojarzonego z accelerator_view z wątku, który utrzymuje blokadę dostępu D3D. Zobacz też scoped_d3d_access_lock, klasę RAII stylu dla zakresu blokowania dostępu D3D.  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view do zablokowania.  
  
##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock  
 Próba uzyskania dostępu D3D blokadę accelerator_view bez blokowania.  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view do zablokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 wartość true, jeśli uzyskano blokady, lub FAŁSZ, jeśli jest on obecnie zajęty przez inny wątek.  
  
##  <a name="d3d_access_unlock"></a>  d3d_access_unlock  
 Zwalnia blokadę D3D dostępu na danym accelerator_view. Jeśli wątek wywołujący nie utrzymuje blokady na accelerator_view wyników jest nieokreślona.  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view, dla którego ma zostać zwolnione blokady.  
  
##  <a name="firstbithigh"></a>  firstbithigh —  
 Pobiera lokalizację pierwszy bit zestawu w _X, zaczynając od bitu najwyższego rzędu i kierunku z bitowego najniższy kolejności.  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Lokalizacja pierwszy bit zestawu  
  
##  <a name="firstbitlow"></a>  firstbitlow —  
 Pobiera lokalizację pierwszy bit zestawu w _X, rozpoczęciem z bitowego najniższy kolejności i pracy bit najwyższej kolejności.  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca położenie pierwszego ustawiony bit  
  
##  <a name="get_buffer"></a>  get_buffer —  
 Pobierz interfejs buforu Direct3D bazowy określonej tablicy.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;  
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementów w tablicy.  
  
 `_Rank`  
 Ranga tablicy.  
  
 `_Array`  
 Tablica accelerator_view Direct3D, dla której jest zwracana powiązanego interfejsu buforu Direct3D.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik interfejsu IUnknown odpowiadający buforu Direct3D bazowy tablicy.  
  
##  <a name="imax"></a>  Imax  
 Określić maksymalną wartość liczbową argumentów  
  
```  
inline int imax(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca maksymalną wartość liczbową argumentów  
  
##  <a name="imin"></a>  imin  
 Określić minimalną wartość liczbową argumentów  
  
```  
inline int imin(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca minimalną wartość liczbowa argumentów  
  
##  <a name="is_timeout_disabled"></a>  is_timeout_disabled  
 Zwraca wartość boolean flagę wskazującą, czy limit czasu jest wyłączona dla określonego accelerator_view. Odpowiada to flaga D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT dla tworzenia urządzenia Direct3D.  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accelerator_view`  
 Accelerator_view, dla których limit czasu wyłączone ustawienie jest można wykonać zapytania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Flaga wartości logicznej wskazująca, czy limit czasu jest wyłączona dla określonego accelerator_view.  
  
##  <a name="mad"></a>  mad —  
 Oblicza iloczyn pierwszego i drugiego określony argument, a następnie dodaje trzeci określonego argumentu.  
  
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
 `_X`  
 Pierwszy argument określony.  
  
 `_Y`  
 Drugi argument określony.  
  
 `_Z`  
 Trzeci argument określony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik `_X`  *  `_Y`  +  `_Z`.  
  
##  <a name="make_array"></a>  make_array —  
 Utwórz tablicy ze wskaźnikiem interfejsu buforu Direct3D.  
  
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
 `value_type`  
 Typ elementu tablicy, która ma zostać utworzony.  
  
 `_Rank`  
 Ranga tablicy ma zostać utworzony.  
  
 `_Extent`  
 Zakres opisującą kształt agregacji tablicy.  
  
 `_Rv`  
 Widok akceleratora D3D, na którym ma być tworzony tablicy.  
  
 `_D3D_buffer`  
 Wskaźnik interfejsu IUnknown do utworzenia tablicy z buforu D3D.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tablica utworzone przy użyciu podanego buforu Direct3D.  
  
##  <a name="noise"></a>  hałasu  
 Generuje losowe wartości przy użyciu algorytmu szumu Perlin  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa, z których można wygenerować szumu Perlin  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość szumu Perlin do zakresu od -1 do 1  
  
##  <a name="radians"></a>  wartość w radianach  
 Konwertuje _X stopnie na radiany  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X skonwertowane z stopnie na radiany  
  
##  <a name="rcp"></a>  rcp  
 Oblicza odwrotność określony argument przy użyciu szybkiego zbliżenia.  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość, dla którego można obliczyć odwrotność.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wzajemne określonego argumentu.  
  
##  <a name="reversebits"></a>  reversebits —  
 Odwraca kolejność bitów w _X  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość liczby całkowitej bez znaku  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość w kolejności bit wycofana w _X  
  
##  <a name="saturate"></a>  saturate —  
 Zawęża _X liczbą z zakresu od 0 do 1  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X zablokowane za pomocą liczbą z zakresu od 0 do 1  
  
##  <a name="sign"></a>  Zaloguj się  
 Określa znak określonego argumentu.  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak argumentu.  
  
##  <a name="smoothstep"></a>  smoothstep —  
 Zwraca smooth interpolacji Hermite od 0 do 1, jeśli _X znajduje się w zakresie [_min —, _maksymalny].  
  
```  
inline float smoothstep(
    float _Min,  
    float _Max,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Min`  
 Wartość zmiennoprzecinkowa  
  
 `_Max`  
 Wartość zmiennoprzecinkowa  
  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli _X jest mniejsza niż _min —; 1, jeśli _X jest większa niż _maksymalny; w przeciwnym razie wartość z zakresu od 0 do 1, jeśli _X znajduje się w zakresie [_min —, _maksymalny]  
  
##  <a name="step"></a>  Krok  
 Porównuje dwie wartości, zwraca 0 lub 1, w oparciu o wartość, która jest większa  
  
```  
inline float step(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 1, jeśli _X jest większa niż lub równa _Y; w przeciwnym razie wartość 0  
  
##  <a name="umax"></a>  UMAX  
 Określić maksymalną wartość liczbową argumentów  
  
```  
inline unsigned int umax(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca maksymalną wartość liczbową argumentów  
  
##  <a name="umin"></a>  umin —  
 Określić minimalną wartość liczbową argumentów  
  
```  
inline unsigned int umin(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca minimalną wartość liczbowa argumentów  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)
