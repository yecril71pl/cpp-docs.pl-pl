---
title: Accelerator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40177af3796a17d32e78e628c41ea694f69ed9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="accelerator-class"></a>accelerator — Klasa
Akceleratora jest możliwość sprzętu, która została zoptymalizowana pod kątem przetwarzania równoległego danych. Akceleratora może być urządzenie podłączone do magistrali PCIe (np. procesora GPU), lub można ją zestawu głównego procesora rozszerzonych instrukcji.  
  
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
|[create_view](#create_view)|Tworzy i zwraca `accelerator_view` obiektu na tego akceleratora.|  
|[get_all](#get_all)|Zwraca wektor `accelerator` obiekty reprezentujące wszystkie dostępne akceleratorów.|  
|[get_auto_selection_view](#get_auto_selection_view)|Zwraca automatyczny wybór `accelerator_view`.|  
|[get_dedicated_memory](#get_dedicated_memory)|Zwraca dedykowanej pamięci dla `accelerator`, w kilobajtach.|  
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Zwraca domyślne [access_type](concurrency-namespace-enums-amp.md#access_type) dla buforów, utworzyć dla tego akceleratora.|  
|[get_default_view](#get_default_view)|Zwraca domyślne `accelerator_view` obiektu, z którym skojarzony jest `accelerator`.|  
|[get_description](#get_description)|Zwraca krótki opis `accelerator` urządzenia.|  
|[get_device_path](#get_device_path)|Zwraca ścieżkę do urządzenia.|  
|[get_has_display](#get_has_display)|Określa, czy `accelerator` jest dołączony do ekranu.|  
|[get_is_debug](#get_is_debug)|Określa, czy `accelerator` ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.|  
|[get_is_emulated](#get_is_emulated)|Określa, czy `accelerator` jest emulowane.|  
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Określa, czy `accelerator` obsługuje udostępniony pamięci|  
|[get_supports_double_precision](#get_supports_double_precision)|Określa, czy `accelerator` jest dołączony do ekranu.|  
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Określa, czy `accelerator` ma ograniczoną obsługę matematyczne podwójnej precyzji.|  
|[get_version](#get_version)|Zwraca wersję `accelerator`.|  
|[set_default](#set_default)|Zwraca ścieżkę domyślnego akceleratora.|  
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Ustawia domyślny Procesor [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic i przydziałów pamięci niejawne wykonanych na tym `accelerator`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Porównuje to `accelerator` obiekt z inną i zwraca `false` , jeśli są takie same; w przeciwnym razie zwraca `true`.|  
|[operator=](#operator_eq)|Kopiuje zawartość określonego `accelerator` obiektu do tego.|  
|[operator==](#operator_eq_eq)|Porównuje to `accelerator` obiekt z inną i zwraca `true` , jeśli są takie same; w przeciwnym razie zwraca `false`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cpu_accelerator](#cpu_accelerator)|Pobiera ciąg stałej dla procesora CPU `accelerator`.|  
|[dedicated_memory](#dedicated_memory)|Pobiera dedykowanej pamięci dla `accelerator`, w kilobajtach.|  
|[default_accelerator](#default_accelerator)|Pobiera ciąg stałej dla domyślnej `accelerator`.|  
|[default_cpu_access_type](#default_cpu_access_type)|Pobiera lub ustawia domyślny Procesor [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic i przydziałów pamięci niejawne wykonanych na tym `accelerator`.|  
|[default_view —](#default_view)|Pobiera domyślny `accelerator_view` obiektu, z którym skojarzony jest `accelerator`.|  
|[Opis elementu](#description)|Pobiera krótki opis `accelerator` urządzenia.|  
|[device_path](#device_path)|Pobiera ścieżkę do urządzenia.|  
|[direct3d_ref](#direct3d_ref)|Pobiera ciąg stałej dla odwołania Direct3D `accelerator`.|  
|[direct3d_warp](#direct3d_warp)|Pobiera ciąg stałej dla `accelerator` obiekt służącego do wykonywania kodu C++ AMP w wielordzeniowych procesorów CPU, które używają Streaming SIMD Extensions (SSE).|  
|[has_display —](#has_display)|Pobiera wartość logiczną wskazującą, czy `accelerator` jest dołączony do ekranu.|  
|[is_debug](#is_debug)|Wskazuje, czy `accelerator` ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.|  
|[is_emulated —](#is_emulated)|Wskazuje, czy `accelerator` jest emulowane.|  
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Wskazuje, czy `accelerator` obsługuje współużytkowana pamięć.|  
|[supports_double_precision](#supports_double_precision)|Wskazuje, czy akceleratora obsługuje matematyczne podwójnej precyzji.|  
|[supports_limited_double_precision](#supports_limited_double_precision)|Wskazuje, czy akceleratora ma ograniczoną obsługę matematyczne podwójnej precyzji.|  
|[Wersja](#version)|Pobiera wersję `accelerator`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `accelerator`  
  
## <a name="remarks"></a>Uwagi  
 Akceleratora jest możliwość sprzętu, która została zoptymalizowana pod kątem przetwarzania równoległego danych. Akceleratora często jest odrębny procesora GPU, ale można też wirtualnego jednostki po stronie hosta, takich jak urządzenia DirectX REF, WARP (Procesora po stronie urządzenia, który jest krótszy, za pomocą instrukcji SSE) lub samego Procesora.  
  
 Można utworzyć `accelerator` obiekt wyliczania dostępnych urządzeń lub pobierania domyślnego urządzenia, odwołanie urządzenie lub urządzenia WARP.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> </a> ~ klawiszy skrótów 

 Niszczy `accelerator` obiektu.  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="ctor"></a> klawiszy skrótów 

 Inicjuje nowe wystąpienie klasy [accelerator — klasa](accelerator-class.md).  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Device_path`  
 Ścieżka urządzenia fizycznego.  
  
 `_Other`  
 Klawiszy skrótów do skopiowania.  
  
##  <a name="cpu_accelerator"></a> cpu_accelerator — 

 Pobiera ciąg stałej akceleratora procesora CPU.  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="create_view"></a> create_view 

 Tworzy i zwraca `accelerator_view` obiektu na tego akceleratora przy użyciu określonego trybu kolejkowania wiadomości. Gdy tryb kolejkowania wiadomości nie jest określona, nowa `accelerator_view` używa [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) tryb kolejkowania wiadomości.  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>Parametry  
 `qmode`  
 Tryb kolejkowania wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowy `accelerator_view` obiektu na tego akceleratora przy użyciu określonego trybu kolejkowania wiadomości.  
  
##  <a name="dedicated_memory"></a> dedicated_memory — 

 Pobiera dedykowanej pamięci dla `accelerator`, w kilobajtach.  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="default_accelerator"></a> default_accelerator — 

 Pobiera ciąg stałej dla domyślnej `accelerator`.  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="default_cpu_access_type"></a> default_cpu_access_type 

 Wartość domyślna procesora [access_type](concurrency-namespace-enums-amp.md#access_type)dla tablic i alokacji pamięci niejawne wprowadzone w tym `accelerator`.  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="default_view"></a> default_view — 

 Pobiera domyślny widok akceleratora, z którym skojarzony jest `accelerator`.  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="description"></a> Opis elementu 

 Pobiera krótki opis `accelerator` urządzenia.  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="device_path"></a> device_path — 

 Pobiera ścieżkę akceleratora. Ścieżka jest unikatowa w systemie.  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="direct3d_ref"></a> direct3d_ref — 

 Pobiera ciąg stałej akceleratora odwołanie Direct3D.  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="direct3d_warp"></a> direct3d_warp — 

 Pobiera ciąg stałej dla `accelerator` obiekt służącego do wykonywania kodu C++ AMP w wielordzeniowych procesorów CPU za pomocą Streaming SIMD Extensions (SSE).  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="get_all"></a> get_all 

 Zwraca wektor `accelerator` obiekty reprezentujące wszystkie dostępne akceleratorów.  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wektor dostępne akceleratorów  
  
##  <a name="get_auto_selection_view"></a> get_auto_selection_view 

 Zwraca accelerator_view Wybór auto, służący określony jako wyniki docelowej parallel_for_each w accelerator_view docelowej wykonania jądra parallel_for_each wybieranych automatycznie w czasie wykonywania. Do innych celów accelerator_view zwracane przez tę metodę jest taka sama jak accelerator_view domyślnego akceleratora domyślne  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Accelerator_view wyboru automatycznego.  
  
##  <a name="get_dedicated_memory"></a> get_dedicated_memory 

 Zwraca dedykowanej pamięci dla `accelerator`, w kilobajtach.  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dedykowanej pamięci dla `accelerator`, w kilobajtach.  
  
##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type 

 Pobiera domyślny access_type procesora cpu dla buforów, utworzyć dla tego akceleratora  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Access_type procesora domyślny dla buforów, utworzyć dla tego akceleratora.  
  
##  <a name="get_default_view"></a> get_default_view 

 Zwraca domyślne `accelerator_view` obiektu, z którym skojarzony jest `accelerator`.  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość domyślna `accelerator_view` obiektu, z którym skojarzony jest `accelerator`.  
  
##  <a name="get_description"></a> get_description 

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
 Ścieżka wystąpienia unikatowych urządzeń całego systemu.  
  
##  <a name="get_has_display"></a> get_has_display 

 Zwraca wartość logiczną wskazującą, czy `accelerator` można danych wyjściowych do wyświetlenia.  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `accelerator` można dane wyjściowe do wyświetlania; w przeciwnym razie `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug 

 Określa, czy `accelerator` ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `accelerator` ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania. W przeciwnym razie `false`.  
  
##  <a name="get_is_emulated"></a> get_is_emulated 

 Określa, czy `accelerator` jest emulowane.  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `accelerator` jest emulowane. W przeciwnym razie `false`.  
  
##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory 

 Zwraca wartość logiczną wskazującą, czy akceleratora obsługuje pamięci dostępne zarówno akceleratora i procesora CPU.  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli akceleratora obsługuje pamięci Procesora udostępnionych. w przeciwnym razie `false`.  
  
##  <a name="get_supports_double_precision"></a> get_supports_double_precision 

 Zwraca wartość logiczną wskazującą, czy akceleratora obsługuje Podwójna precyzja matematyczne, w tym zespolone mnożenia dodać (FMA) dzielenia, odwrotność i rzutowanie między `int` i `double`.  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli akceleratora obsługuje Podwójna precyzja matematyczne; w przeciwnym razie `false`.  
  
##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision 

 Zwraca wartość logiczną, wskazującą, czy akceleratora ma ograniczoną obsługę Podwójna precyzja matematycznych. Jeśli akceleratora ma tylko ograniczoną obsługę, następnie zespolone mnożenie (FMA), Dodaj dzielenia, odwrotność i rzutowanie między `int` i `double` nie są obsługiwane.  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli akceleratora ma ograniczoną obsługę Podwójna precyzja matematyczne; w przeciwnym razie `false`.  
  
##  <a name="get_version"></a> get_version 

 Zwraca wersję `accelerator`.  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wersja `accelerator`.  
  
##  <a name="has_display"></a> has_display — 

 Pobiera wartość logiczną wskazującą, czy `accelerator` można danych wyjściowych do wyświetlenia.  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="is_debug"></a> is_debug — 

 Pobiera wartość logiczną wskazującą, czy `accelerator` ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="is_emulated"></a> is_emulated — 

 Pobiera wartość logiczną wskazującą, czy `accelerator` jest emulowane.  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="operator_neq"></a> operator! = 

 Porównuje to `accelerator` obiekt z inną i zwraca `false` , jeśli są takie same; w przeciwnym razie zwraca `true`.  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `false` Jeśli dwa `accelerator` obiekty są takie same; w przeciwnym razie `true`.  
  
##  <a name="operator_eq"></a> operator = 

 Kopiuje zawartość określonego `accelerator` obiektu do tego.  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `accelerator` obiektu.  
  
##  <a name="operator_eq_eq"></a> operator == 

 Porównuje to `accelerator` obiekt z inną i zwraca `true` , jeśli są takie same; w przeciwnym razie zwraca `false`.  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli drugiej `accelerator` obiekt jest taki sam jak to `accelerator` obiektu; w przeciwnym razie `false`.  
  
##  <a name="set_default"></a> set_default 

 Ustawia domyślnego akceleratora służący do żadnej operacji, która niejawnie korzysta z domyślnego akceleratora. Ta metoda powiedzie się tylko, jeśli akceleratora domyślną środowiska uruchomieniowego nie ma już używane w przypadku operacji, która niejawnie korzysta z domyślnego akceleratora  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>Parametry  
 `_Path`  
 Ścieżka do akceleratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wywołanie zakończy się pomyślnie na ustawienie domyślnego akceleratora. W przeciwnym razie `false`.  
  
##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type 

 Ustaw domyślny access_type procesora cpu dla tablic utworzone dla tego akceleratora lub dla przydziału pamięci niejawne jako część array_views dostęp do tego akceleratora na tym. Ta metoda powiedzie się tylko, jeśli default_cpu_access_type dla akcelerator nie została już przesłonięta przez poprzednie wywołanie tej metody i default_cpu_access_type środowiska uruchomieniowego wybrany dla tego akceleratora nie jeszcze został użyty do przydzielania tablicy lub Alokacja pamięci niejawne kopii array_view — dostępny na ten akcelerator.  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>Parametry  
 `_Default_cpu_access_type`  
 Access_type procesora domyślne służący do tablicy/array_view — alokacje pamięci dla tego akceleratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczną wskazującą, czy pomyślnie ustawiono domyślne access_type procesora cpu dla akceleratora.  
  
##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory 

 Pobiera wartość Boolean wskazującą czy `accelerator` obsługuje współużytkowana pamięć.  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="supports_double_precision"></a> supports_double_precision 

 Pobiera wartość logiczną wskazującą, czy akceleratora obsługuje matematyczne podwójnej precyzji.  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision 

 Pobiera wartość logiczną wskazującą, czy akceleratora ma ograniczoną obsługę Podwójna precyzja matematycznych. Jeśli akceleratora ma tylko ograniczoną obsługę, następnie zespolone mnożenie (FMA), Dodaj dzielenia, odwrotność i rzutowanie między `int` i `double` nie są obsługiwane.  
  
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
  
##  <a name="accelerator"></a> klawiszy skrótów 

 Pobiera `accelerator` obiekt do [accelerator_view](accelerator-view-class.md) obiektu.  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="ctor"></a> accelerator_view 

 Inicjuje nowe wystąpienie klasy [accelerator_view](accelerator-view-class.md) przez skopiowanie istniejącej `accelerator_view` obiektu.  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiektu do skopiowania.  
  
##  <a name="create_marker"></a> create_marker 

 Zwraca przyszłości na ukończenie wszystkich poleceń przesłane do tej pory tej ścieżki `accelerator_view` obiektu.  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyszłe na ukończenie wszystkich poleceń przesłane do tej pory tej ścieżki `accelerator_view` obiektu.  
  
##  <a name="flush"></a> Flush 

 Przesyła wszystkie oczekujące poleceń w kolejce do [accelerator_view](accelerator-view-class.md) obiekt do skrótów do wykonania.  
  
```  
void flush();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `void`.  
  
##  <a name="get_accelerator"></a> get_accelerator 

 Zwraca `accelerator` obiekt do [accelerator_view](accelerator-view-class.md) obiektu.  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `accelerator` Obiekt do `accelerator_view` obiektu.  
  
##  <a name="get_is_auto_selection"></a> get_is_auto_selection 

 Zwraca wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednie akcelerator podczas accelerator_view jest przekazywana do [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli środowisko uruchomieniowe automatycznie wybierze odpowiednie akcelerator; w przeciwnym razie `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug 

 Zwraca wartość logiczną wskazującą, czy [accelerator_view](accelerator-view-class.md) obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna, która wskazuje, czy `accelerator_view` obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
##  <a name="get_queuing_mode"></a> get_queuing_mode 

 Zwraca tryb kolejkowania [accelerator_view](accelerator-view-class.md) obiektu.  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tryb kolejkowania `accelerator_view` obiektu.  
  
##  <a name="get_version"></a> get_version 

 Zwraca wersję [accelerator_view](accelerator-view-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wersja `accelerator_view`.  
  
##  <a name="is_auto_selection"></a> is_auto_selection 

 Pobiera wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednie akcelerator podczas accelerator_view jest przekazywana do [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="is_debug"></a> is_debug — 

 Pobiera wartość logiczną wskazującą, czy [accelerator_view](accelerator-view-class.md) obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="operator_neq"></a> operator! = 

 Porównuje to [accelerator_view](accelerator-view-class.md) obiekt z inną i zwraca `false` , jeśli są takie same; w przeciwnym razie zwraca `true`.  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `false` Jeśli dwa obiekty są takie same; w przeciwnym razie `true`.  
  
##  <a name="operator_eq"></a> operator = 

 Kopiuje zawartość określonego [accelerator_view](accelerator-view-class.md) obiektu do tego.  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do modyfikacji `accelerator_view` obiektu.  
  
##  <a name="operator_eq_eq"></a> operator == 

 Porównuje to [accelerator_view](accelerator-view-class.md) obiekt z inną i zwraca `true` , jeśli są takie same; w przeciwnym razie zwraca `false`.  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli dwa obiekty są takie same; w przeciwnym razie `false`.  
  
##  <a name="queuing_mode"></a> queuing_mode 

 Pobiera tryb kolejkowania [accelerator_view](accelerator-view-class.md) obiektu.  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="version"></a> Wersja 

 Pobiera wersję [accelerator_view](accelerator-view-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="wait"></a> oczekiwania 

 Czeka na wszystkie polecenia przesłane do [accelerator_view](accelerator-view-class.md) obiekt, aby zakończyć.  
  
```  
void wait();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `void`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
