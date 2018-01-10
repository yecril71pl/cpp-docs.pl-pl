---
title: "accelerator_view — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs: C++
helpviewer_keywords: accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fd05acc351a23cc088c6491a76ecfb91583b16b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="acceleratorview-class"></a>accelerator_view — Klasa
Reprezentuje abstrakcji urządzenia wirtualnego na akceleratora równoległe danych C++ AMP.  
  
### <a name="syntax"></a>Składnia  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accelerator_view — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view` klasy.|  
|[~ accelerator_view — destruktor](#dtor)|Niszczy `accelerator_view` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[create_marker](#create_marker)|Zwraca przyszłości na ukończenie wszystkich poleceń przesłane do tej pory tej ścieżki `accelerator_view` obiektu.|  
|[Flush](#flush)|Przesyła wszystkie oczekujące poleceń w kolejce w celu `accelerator_view` obiekt do skrótów do wykonania.|  
|[get_accelerator](#get_accelerator)|Zwraca `accelerator` obiekt do `accelerator_view` obiektu.|  
|[get_is_auto_selection](#get_is_auto_selection)|Zwraca wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednią akcelerator podczas `accelerator_view` obiekt jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[get_is_debug](#get_is_debug)|Zwraca wartość logiczną wskazującą, czy `accelerator_view` obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.|  
|[get_queuing_mode](#get_queuing_mode)|Zwraca tryb kolejkowania `accelerator_view` obiektu.|  
|[get_version](#get_version)|Zwraca wersję `accelerator_view`.|  
|[oczekiwania](#wait)|Czeka na wszystkie polecenia przesłane do `accelerator_view` obiekt, aby zakończyć.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Porównuje to `accelerator_view` obiekt z inną i zwraca `false` , jeśli są takie same; w przeciwnym razie zwraca `true`.|  
|[operator =](#operator_eq)|Kopiuje zawartość określonego `accelerator_view` obiektu do tego.|  
|[operator ==](#operator_eq_eq)|Porównuje to `accelerator_view` obiekt z inną i zwraca `true` , jeśli są takie same; w przeciwnym razie zwraca `false`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[klawiszy skrótów](#accelerator)|Pobiera `accelerator` obiekt do `accelerator_view` obiektu.|  
|[is_auto_selection](#is_auto_selection)|Pobiera wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednią akcelerator podczas `accelerator_view` obiekt jest przekazywany do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[is_debug —](#is_debug)|Pobiera wartość logiczną wskazującą, czy `accelerator_view` obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.|  
|[queuing_mode —](#queuing_mode)|Pobiera tryb kolejkowania `accelerator_view` obiektu.|  
|[Wersja](#version)|Pobiera wersję akceleratora.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `accelerator_view`  
  
### <a name="remarks"></a>Uwagi  
 `accelerator_view` Obiekt reprezentuje logiczne, izolowanego widok akceleratora. Urządzenie jednego fizycznego obliczeń może mieć wiele logicznych, izolowanego `accelerator_view` obiektów. Każdy akceleratora ma wartość domyślną `accelerator_view` obiektu. Dodatkowe `accelerator_view` obiekty mogą być tworzone.  
  
 Fizyczne urządzenia mogą być współużytkowane przez wiele wątków klienta. Wątki klientów wspólnie można używać tego samego `accelerator_view` obiektu akceleratora lub każdy klient może komunikować się z urządzenie obliczeniowe za pośrednictwem niezależne `accelerator_view` obiektu dla odizolowanie od innych wątków klienta.  
  
 `accelerator_view` Obiekt może mieć jedną z dwóch [queuing_mode — wyliczenie](concurrency-namespace-enums-amp.md#queuing_mode) stanów. Jeśli tryb kolejkowania wiadomości jest `immediate`, takich jak polecenia `copy` i `parallel_for_each` są wysyłane do odpowiedniego urządzenia akceleratora, jak tylko zostaną zwrócone do obiektu wywołującego. Jeśli tryb kolejkowania wiadomości jest `deferred`, tych poleceń są umieszczone w kolejce w kolejce polecenia, który odpowiada `accelerator_view` obiektu. Polecenia faktycznie nie wysyłane do urządzenia do momentu `flush()` jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  

## <a name="accelerator"></a>klawiszy skrótów 

Pobiera obiekt akceleratora dla obiekt accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="ctor"></a>accelerator_view 

Inicjuje nowe wystąpienie klasy accelerator_view przez skopiowanie istniejącej `accelerator_view` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiektu do skopiowania.  
  
## <a name="accelerator_view__create_marker"></a>create_marker 

Zwraca przyszłości na ukończenie wszystkich poleceń przesłane do tej pory tej ścieżki `accelerator_view` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyszłe na ukończenie wszystkich poleceń przesłane do tej pory tej ścieżki `accelerator_view` obiektu.  
  
## <a name="flush"></a>Flush 

Przesyła się, że wszystkie polecenia oczekujących w kolejce do obiektu accelerator_view do skrótów do wykonania.  
  
### <a name="syntax"></a>Składnia  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `void`.  

## <a name="accelerator_view__get_accelerator"></a>get_accelerator 

Zwraca obiekt akceleratora dla obiekt accelerator_view.
### <a name="syntax"></a>Składnia
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Wartość zwracana
Obiekt akceleratora dla obiekt accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a>get_is_auto_selection 

Zwraca wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednie akcelerator podczas accelerator_view jest przekazywana do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Składnia  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli środowisko uruchomieniowe automatycznie wybierze odpowiednie akcelerator; w przeciwnym razie `false`.  
  
## <a name="accelerator_view__get_is_debug"></a>get_is_debug 

Zwraca wartość logiczną, wskazującą, czy obiekt accelerator_view ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna, która wskazuje, czy `accelerator_view` obiektu jest włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  

## <a name="accelerator_view__get_queuing_mode"></a>get_queuing_mode 

Zwraca tryb kolejkowania dla obiekt accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tryb kolejkowania `accelerator_view` obiektu.  
  
## <a name="accelerator_view__get_version"></a>get_version 

Zwraca wersję accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wersja `accelerator_view`.  
  
## <a name="accelerator_view__is_auto_selection"></a>is_auto_selection 

Pobiera wartość logiczną wskazującą, czy środowisko uruchomieniowe automatycznie wybiera odpowiednie akcelerator podczas accelerator_view jest przekazywana do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="accelerator_view__is_debug"></a>is_debug — 

Pobiera wartość logiczną wskazującą, czy obiekt accelerator_view ma włączone dla usługi raportowania błędów szeroką gamę warstwy debugowania.  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="accelerator_view__operator_neq"></a>operator! = 

Ten obiekt accelerator_view innym porównuje i zwraca `false` , jeśli są takie same; w przeciwnym razie zwraca `true`.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `false`Jeśli dwa obiekty są takie same; w przeciwnym razie `true`.  
  
## <a name="accelerator_view__operator_eq"></a>operator = 

Kopiuje zawartość accelerator_view określony obiekt do tego.  
  
### <a name="syntax"></a>Składnia  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do modyfikacji `accelerator_view` obiektu.  
  
## <a name="accelerator_view__operator_eq_eq"></a>operator == 

Ten obiekt accelerator_view innym porównuje i zwraca `true` , jeśli są takie same; w przeciwnym razie zwraca `false`.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Obiekt do porównania z tym kontem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli dwa obiekty są takie same; w przeciwnym razie `false`.  
  
## <a name="accelerator_view__queuing_mode"></a>queuing_mode — 

Pobiera tryb kolejkowania dla obiekt accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="accelerator_view__version"></a>Wersja 

Pobiera wersję accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="accelerator_view__wait"></a>oczekiwania 

Czeka na wszystkie polecenia przesłane do obiektów accelerator_view zakończyć.  
  
### <a name="syntax"></a>Składnia  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 Zwraca `void`.  
  
#### <a name="remarks"></a>Uwagi  
 Jeśli [queuing_mode —](concurrency-namespace-enums-amp.md#queuing_mode) jest `immediate`, ta metoda zwraca się natychmiast bez blokowania.  
  
##  <a name="dtor"></a>~ accelerator_view 

 Niszczy obiektów accelerator_view.  
  
#### <a name="syntax"></a>Składnia  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
 
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
