---
title: "Przestrzeń nazw platformy (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Platform/Platform
dev_langs: C++
helpviewer_keywords: Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d434d687eca53deb4cad41615fcfd676836dda5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platform-namespace-ccx"></a>Przestrzeń nazw platformy (C + +/ CX)
Zawiera wbudowane typy, które są zgodne z środowiska uruchomieniowego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
using namespace Platform;  
```  
  
### <a name="members"></a>Elementy członkowskie  
 **Atrybuty**  
  
 Przestrzeń nazw platformy zawiera atrybuty, klas, wyliczeń, interfejsów i struktury. Platforma zawiera również zagnieżdżonej przestrzeni nazw.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Flagi|Wskazuje, że wyliczenie może być traktowana jako pole bitowe; oznacza to, że zestaw flag.|  
|MTAThread|Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).|  
|STAThread|Wskazuje, że model wątkowy dla aplikacji jest jednowątkowego apartamentu (STA).|  
  
 **Klasy**  
  
 Przestrzeń nazw platformy ma następujące klasy.  
  
|Class|Opis|  
|-----------|-----------------|  
|[Platform::AccessDeniedException, klasa](../cppcx/platform-accessdeniedexception-class.md)|Wywoływane, gdy odmowa dostępu do zasobów lub funkcji.|  
|[Platform::Agile, klasa](../cppcx/platform-agile-class.md)|Reprezentuje obiekt agile jako obiekt elastyczne.|  
|[Platform::Array, klasa](../cppcx/platform-array-class.md)|Reprezentuje tablicą jednowymiarową, można modyfikować.|  
|[Platform::ArrayReference, klasa](../cppcx/platform-arrayreference-class.md)|Reprezentuje tablicę, których inicjowanie jest zoptymalizowany do zminimalizowania operacji kopiowania.|  
|[Platform::Box, klasa](../cppcx/platform-box-class.md)|Używane do deklarowania typu opakowanego, który hermetyzuje typu wartości, takich jak Windows::Foundation::DateTime lub int64, gdy tego typu jest przekazywane przez interfejs binarne aplikacji (ABI) lub przechowywane w zmiennej typu [Platform::Object ^](../cppcx/platform-object-class.md).|  
|[Platform::ChangedStateException, klasa](../cppcx/platform-changedstateexception-class.md)|Element zgłaszany, gdy metody iterator kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, unieważnia wyniki metody.|  
|[Platform::ClassNotRegisteredException, klasa](../cppcx/platform-classnotregisteredexception-class.md)|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|  
|[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)|Reprezentuje wyjątek zgłaszany, gdy nierozpoznaną wartość jest zwracana z wywołania metody COM.|  
|[Platform::Delegate, klasa](../cppcx/platform-delegate-class.md)|Reprezentuje podpis funkcji wywołania zwrotnego.|  
|[Platform::DisconnectedException, klasa](../cppcx/platform-disconnectedexception-class.md)|Obiekt został odłączony od swoich klientów.|  
|[Platform::Exception, klasa](../cppcx/platform-exception-class.md)|Reprezentuje błędów występujących podczas wykonywania aplikacji. Klasa podstawowa dla wyjątków.|  
|[Platform::FailureException, klasa](../cppcx/platform-failureexception-class.md)|Element zgłaszany, gdy operacja nie powiodła się. Jest odpowiednikiem E_FAIL HRESULT.|  
|[Platform::Guid, klasa wartości](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID w systemie typów środowiska wykonawczego systemu Windows.|  
|[Platform::InvalidArgumentException, klasa](../cppcx/platform-invalidargumentexception-class.md)|Element zgłaszany, gdy jedna z podanych argumentów metody jest nieprawidłowa.|  
|[Platform::InvalidCastException, klasa](../cppcx/platform-invalidcastexception-class.md)|Element zgłaszany w przypadku Nieprawidłowe rzutowanie lub jawnej konwersji.|  
|[Platform::MTAThreadAttribute, klasa](../cppcx/platform-mtathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).|  
|[Platform::NotImplementedException, klasa](../cppcx/platform-notimplementedexception-class.md)|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|  
|[Platform::NullReferenceException, klasa](../cppcx/platform-nullreferenceexception-class.md)|Element zgłaszany, gdy jest próba wyłuskania odwołanie do obiektu o wartości null.|  
|[Platform::Object, klasa](../cppcx/platform-object-class.md)|Klasa podstawowa zawiera wspólnego zachowania.|  
|[Platform::ObjectDisposedException, klasa](../cppcx/platform-objectdisposedexception-class.md)|Element zgłaszany, gdy operacja jest wykonywana na zlikwidowanym obiekcie.|  
|[Platform::OperationCanceledException, klasa](../cppcx/platform-operationcanceledexception-class.md)|Element zgłaszany, gdy operacja została przerwana.|  
|[Platform::OutOfBoundsException, klasa](../cppcx/platform-outofboundsexception-class.md)|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|  
|[Platform::OutOfMemoryException, klasa](../cppcx/platform-outofmemoryexception-class.md)|Element zgłaszany, gdy jest za mało pamięci do ukończenia tej operacji.|  
|[Platform::STAThreadAttribute, klasa](../cppcx/platform-stathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest jednowątkowego apartamentu (STA).|  
|[Platform::String, klasa](../cppcx/platform-string-class.md)|Sekwencyjną kolekcją znaków Unicode, który jest używany do reprezentowania tekstu.|  
|[Platform::StringReference, klasa](../cppcx/platform-stringreference-class.md)|Zapewnia dostęp do buforów ciągu z co najmniej narzut kopiowania.|  
|[Platform::Type, klasa](../cppcx/platform-type-class.md)|Określa typ wbudowany przez wyliczenie kategorii.|  
|[Platform::ValueType, klasa](../cppcx/platform-valuetype-class.md)|Klasa podstawowa dla wystąpień typów wartości.|  
|[Platform::WeakReference, klasa](../cppcx/platform-weakreference-class.md)|Udostępnia słabe odwołanie do obiektów klasy ref, który nie zwiększa się liczba odwołań.|  
|[Platform::WriteOnlyArray, klasa](../cppcx/platform-writeonlyarray-class.md)|Reprezentuje Jednowymiarowa tablica tylko do zapisu, który jest używany jako parametr wejściowy dla metod, które implementują wzorzec FillArray.|  
|[Platform::WrongThreadException, klasa](../cppcx/platform-wrongthreadexception-class.md)|Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu dla obiekt serwera proxy, który nie należy do apartamentu wątku.|  
  
 **Implementacje interfejsu**  
  
 Przestrzeń nazw platformy definiuje następujące interfejsy.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[Platform::IBox, interfejs](../cppcx/platform-ibox-interface.md)|Służy do przekazywania typów wartości do funkcji, której parametry są wpisywane jako Platform::Object ^.|  
|[Platform::IBoxArray, interfejs](../cppcx/platform-iboxarray-interface.md)|Interfejs używany do przekazania do funkcji, której parametry są wpisywane jako Platform::Array tablice typów wartości.|  
|[Platform::IDisposable, interfejs](../cppcx/platform-idisposable-interface.md)|Należy użyć, aby zwolnić zasoby niezarządzane.|  
  
 **Wyliczenia**  
  
 Przestrzeń nazw platformy ma następujące wyliczenia.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[Platform::CallbackContext, wyliczenie](../cppcx/platform-callbackcontext-enumeration.md)|Wyliczenie używany jako parametr konstruktora delegata. Określają one, czy ma być skierowany do źródłowego wątku lub wątek wywołujący wywołania zwrotnego.|  
|[Platform::TypeCode, wyliczenie](../cppcx/platform-typecode-enumeration.md)|Określa liczbowych kategorię, która reprezentuje typ wbudowany.|  
  
 **Struktury**  
  
 Przestrzeń nazw platformy ma następujące struktury.  
  
|Struktura|Opis|  
|---------------|-----------------|  
|[Platform::Enum, klasa](../cppcx/platform-enum-class.md)|Reprezentuje nazwanej stałej.|  
|[Platform::Guid, klasa wartości](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID.|  
|[Platform::IntPtr, klasa wartości](../cppcx/platform-intptr-value-class.md)|Podpisem wskaźnik, którego rozmiar jest odpowiedni dla platformy (32-bitowy lub 64-bitowe).|  
|[Platform::SizeT, klasa wartości](../cppcx/platform-sizet-value-class.md)|Typ danych bez znaku, używany do reprezentowania rozmiar obiektu.|  
|[Platform::UIntPtr, klasa wartości](../cppcx/platform-uintptr-value-class.md)|Wskaźnika bez znaku, którego rozmiar jest odpowiedni dla platformy (32-bitowy lub 64-bitowe).|  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Namespace platform::Runtime::CompilerServices](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Namespace platform::Runtime::InteropServices](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Platform::Metadata, przestrzeń nazw](../cppcx/platform-metadata-namespace.md)