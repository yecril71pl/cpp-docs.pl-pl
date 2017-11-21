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
ms.openlocfilehash: 850156c2db7e57a357b1fa68337753ebd37db30d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Klasa platform::AccessDeniedException](../cppcx/platform-accessdeniedexception-class.md)|Wywoływane, gdy odmowa dostępu do zasobów lub funkcji.|  
|[Klasa platform::Agile](../cppcx/platform-agile-class.md)|Reprezentuje obiekt agile jako obiekt elastyczne.|  
|[Klasa platform::Array](../cppcx/platform-array-class.md)|Reprezentuje tablicą jednowymiarową, można modyfikować.|  
|[Klasa platform::ArrayReference](../cppcx/platform-arrayreference-class.md)|Reprezentuje tablicę, których inicjowanie jest zoptymalizowany do zminimalizowania operacji kopiowania.|  
|[Klasa platform::Box](../cppcx/platform-box-class.md)|Używane do deklarowania typu opakowanego, który hermetyzuje typu wartości, takich jak Windows::Foundation::DateTime lub int64, gdy tego typu jest przekazywane przez interfejs binarne aplikacji (ABI) lub przechowywane w zmiennej typu [Platform::Object ^](../cppcx/platform-object-class.md).|  
|[Klasa platform::ChangedStateException](../cppcx/platform-changedstateexception-class.md)|Element zgłaszany, gdy metody iterator kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, unieważnia wyniki metody.|  
|[Klasa platform::ClassNotRegisteredException](../cppcx/platform-classnotregisteredexception-class.md)|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|  
|[Klasa platform::COMException](../cppcx/platform-comexception-class.md)|Reprezentuje wyjątek zgłaszany, gdy nierozpoznaną wartość jest zwracana z wywołania metody COM.|  
|[Klasa platform::Delegate](../cppcx/platform-delegate-class.md)|Reprezentuje podpis funkcji wywołania zwrotnego.|  
|[Klasa platform::DisconnectedException](../cppcx/platform-disconnectedexception-class.md)|Obiekt został odłączony od swoich klientów.|  
|[Klasa platform::Exception](../cppcx/platform-exception-class.md)|Reprezentuje błędów występujących podczas wykonywania aplikacji. Klasa podstawowa dla wyjątków.|  
|[Klasa platform::FailureException](../cppcx/platform-failureexception-class.md)|Element zgłaszany, gdy operacja nie powiodła się. Jest odpowiednikiem E_FAIL HRESULT.|  
|[Klasa wartości platform::GUID](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID w systemie typów środowiska wykonawczego systemu Windows.|  
|[Klasa platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md)|Element zgłaszany, gdy jedna z podanych argumentów metody jest nieprawidłowa.|  
|[Klasa platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md)|Element zgłaszany w przypadku Nieprawidłowe rzutowanie lub jawnej konwersji.|  
|[Klasa platform::MTAThreadAttribute](../cppcx/platform-mtathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).|  
|[Klasa platform::NotImplementedException](../cppcx/platform-notimplementedexception-class.md)|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|  
|[Klasa platform::NullReferenceException](../cppcx/platform-nullreferenceexception-class.md)|Element zgłaszany, gdy jest próba wyłuskania odwołanie do obiektu o wartości null.|  
|[Klasa platform::Object](../cppcx/platform-object-class.md)|Klasa podstawowa zawiera wspólnego zachowania.|  
|[Klasa platform::ObjectDisposedException](../cppcx/platform-objectdisposedexception-class.md)|Element zgłaszany, gdy operacja jest wykonywana na zlikwidowanym obiekcie.|  
|[Klasa platform::OperationCanceledException](../cppcx/platform-operationcanceledexception-class.md)|Element zgłaszany, gdy operacja została przerwana.|  
|[Klasa platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md)|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|  
|[Klasa platform::OutOfMemoryException](../cppcx/platform-outofmemoryexception-class.md)|Element zgłaszany, gdy jest za mało pamięci do ukończenia tej operacji.|  
|[Klasa platform::STAThreadAttribute](../cppcx/platform-stathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest jednowątkowego apartamentu (STA).|  
|[Klasa platform::String](../cppcx/platform-string-class.md)|Sekwencyjną kolekcją znaków Unicode, który jest używany do reprezentowania tekstu.|  
|[Klasa platform::StringReference](../cppcx/platform-stringreference-class.md)|Zapewnia dostęp do buforów ciągu z co najmniej narzut kopiowania.|  
|[Klasa platform::type](../cppcx/platform-type-class.md)|Określa typ wbudowany przez wyliczenie kategorii.|  
|[Klasa platform::ValueType](../cppcx/platform-valuetype-class.md)|Klasa podstawowa dla wystąpień typów wartości.|  
|[Klasa platform::WeakReference](../cppcx/platform-weakreference-class.md)|Udostępnia słabe odwołanie do obiektów klasy ref, który nie zwiększa się liczba odwołań.|  
|[Klasa platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)|Reprezentuje Jednowymiarowa tablica tylko do zapisu, który jest używany jako parametr wejściowy dla metod, które implementują wzorzec FillArray.|  
|[Klasa platform::WrongThreadException](../cppcx/platform-wrongthreadexception-class.md)|Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu dla obiekt serwera proxy, który nie należy do apartamentu wątku.|  
  
 **Implementacje interfejsu**  
  
 Przestrzeń nazw platformy definiuje następujące interfejsy.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[Interfejs platform::IBox](../cppcx/platform-ibox-interface.md)|Służy do przekazywania typów wartości do funkcji, której parametry są wpisywane jako Platform::Object ^.|  
|[Interfejs platform::IBoxArray](../cppcx/platform-iboxarray-interface.md)|Interfejs używany do przekazania do funkcji, której parametry są wpisywane jako Platform::Array tablice typów wartości.|  
|[Interfejs platform::IDisposable](../cppcx/platform-idisposable-interface.md)|Należy użyć, aby zwolnić zasoby niezarządzane.|  
  
 **Wyliczenia**  
  
 Przestrzeń nazw platformy ma następujące wyliczenia.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[Platform::CallbackContext — wyliczenie](../cppcx/platform-callbackcontext-enumeration.md)|Wyliczenie używany jako parametr konstruktora delegata. Określają one, czy ma być skierowany do źródłowego wątku lub wątek wywołujący wywołania zwrotnego.|  
|[Platform::TypeCode — wyliczenie](../cppcx/platform-typecode-enumeration.md)|Określa liczbowych kategorię, która reprezentuje typ wbudowany.|  
  
 **Struktury**  
  
 Przestrzeń nazw platformy ma następujące struktury.  
  
|Struktura|Opis|  
|---------------|-----------------|  
|[Klasa platform::Enum](../cppcx/platform-enum-class.md)|Reprezentuje nazwanej stałej.|  
|[Klasa wartości platform::GUID](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID.|  
|[Klasa wartości platform::IntPtr](../cppcx/platform-intptr-value-class.md)|Podpisem wskaźnik, którego rozmiar jest odpowiedni dla platformy (32-bitowy lub 64-bitowe).|  
|[Klasa wartości platform::sizet](../cppcx/platform-sizet-value-class.md)|Typ danych bez znaku, używany do reprezentowania rozmiar obiektu.|  
|[Klasa wartości platform::UIntPtr](../cppcx/platform-uintptr-value-class.md)|Wskaźnika bez znaku, którego rozmiar jest odpowiedni dla platformy (32-bitowy lub 64-bitowe).|  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Namespace platform::Runtime::CompilerServices](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Namespace platform::Runtime::InteropServices](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Namespace platform::METADATA](../cppcx/platform-metadata-namespace.md)