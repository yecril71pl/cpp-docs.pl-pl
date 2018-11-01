---
title: Przestrzeń nazw platformy (C + +/ CX)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform/Platform
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
ms.openlocfilehash: e5d2caa4e784d7d8f7589bca0ef5210c03cb0d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523876"
---
# <a name="platform-namespace-ccx"></a>Przestrzeń nazw platformy (C + +/ CX)

Zawiera wbudowane typy, które są zgodne ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```cpp
using namespace Platform;
```

### <a name="members"></a>Elementy członkowskie

**Atrybuty**

Przestrzeń nazw platformy zawiera atrybuty, klas, wyliczeń, interfejsy i struktur. Platforma również zawiera zagnieżdżone przestrzenie nazw.

|Atrybut|Opis|
|---------------|-----------------|
|Flagi|Wskazuje, że wyliczenie może być traktowana jako pole bitowe; oznacza to, że zestaw flag.|
|MTAThread|Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).|
|STAThread|Wskazuje, że model wątkowy dla aplikacji jest jednowątkowym (przedziale STA).|

**Klasy**

Przestrzeń nazw platformy ma następujące klasy.

|Class|Opis|
|-----------|-----------------|
|[Platform::AccessDeniedException, klasa](../cppcx/platform-accessdeniedexception-class.md)|Wywoływane, gdy są odmowa dostępu do zasobów lub funkcji.|
|[Platform::Agile, klasa](../cppcx/platform-agile-class.md)|Reprezentuje obiekt agile jako obiekt agile.|
|[Platform::Array, klasa](../cppcx/platform-array-class.md)|Reprezentuje tablicę jednowymiarową, którą można modyfikować.|
|[Platform::ArrayReference, klasa](../cppcx/platform-arrayreference-class.md)|Reprezentuje tablicę, której inicjowania jest zoptymalizowany do zminimalizowania operacji kopiowania.|
|[Platform::Box, klasa](../cppcx/platform-box-class.md)|Używane do deklarowania typ spakowany, który hermetyzuje typ wartości, takich jak Windows::Foundation::DateTime lub int64 w przypadku tego typu jest przekazywana między interfejsem binarnym aplikacji (ABI) lub przechowywane w zmiennej typu [Platform::Object ^](../cppcx/platform-object-class.md).|
|[Platform::ChangedStateException, klasa](../cppcx/platform-changedstateexception-class.md)|Element zgłaszany, gdy metody iteratora kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, powodując unieważnienie wyniki metody.|
|[Platform::ClassNotRegisteredException, klasa](../cppcx/platform-classnotregisteredexception-class.md)|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|
|[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)|Reprezentuje wyjątek, który jest generowany, gdy obsahuje nerozpoznanou hodnotu jest zwracany z wywołania metody COM.|
|[Platform::Delegate, klasa](../cppcx/platform-delegate-class.md)|Reprezentuje podpis funkcji wywołania zwrotnego.|
|[Platform::DisconnectedException, klasa](../cppcx/platform-disconnectedexception-class.md)|Obiekt został odłączony od swoich klientów.|
|[Platform::Exception, klasa](../cppcx/platform-exception-class.md)|Reprezentuje błędy występujące podczas wykonywania aplikacji. Klasa bazowa dla wyjątków.|
|[Platform::FailureException, klasa](../cppcx/platform-failureexception-class.md)|Element zgłaszany, gdy operacja nie powiodła się. Jest odpowiednikiem E_FAIL HRESULT.|
|[Platform::Guid, klasa wartości](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID w systemie typów środowiska wykonawczego Windows.|
|[Platform::InvalidArgumentException, klasa](../cppcx/platform-invalidargumentexception-class.md)|Element zgłaszany, gdy jeden z podanych argumentów metody jest nieprawidłowy.|
|[Platform::InvalidCastException, klasa](../cppcx/platform-invalidcastexception-class.md)|Element zgłaszany w przypadku Nieprawidłowe rzutowanie lub konwersji jawnej.|
|[Platform::MTAThreadAttribute, klasa](../cppcx/platform-mtathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).|
|[Platform::NotImplementedException, klasa](../cppcx/platform-notimplementedexception-class.md)|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|
|[Platform::NullReferenceException, klasa](../cppcx/platform-nullreferenceexception-class.md)|Zgłaszany, gdy jest próba wyłuskania odwołanie do obiektu o wartości null.|
|[Platform::Object, klasa](../cppcx/platform-object-class.md)|Klasa bazowa, który zawiera wspólnego zachowania.|
|[Platform::ObjectDisposedException, klasa](../cppcx/platform-objectdisposedexception-class.md)|Element zgłaszany, gdy operacja jest wykonywana na zlikwidowanego obiektu.|
|[Platform::OperationCanceledException, klasa](../cppcx/platform-operationcanceledexception-class.md)|Element zgłaszany, gdy operacja została przerwana.|
|[Platform::OutOfBoundsException, klasa](../cppcx/platform-outofboundsexception-class.md)|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|[Platform::OutOfMemoryException, klasa](../cppcx/platform-outofmemoryexception-class.md)|Element zgłaszany, gdy ma za mało pamięci do ukończenia tej operacji.|
|[Platform::STAThreadAttribute, klasa](../cppcx/platform-stathreadattribute-class.md)|Wskazuje, że model wątkowy dla aplikacji jest jednowątkowym (przedziale STA).|
|[Platform::String, klasa](../cppcx/platform-string-class.md)|Sekwencyjną kolekcją znaków Unicode, który jest używany do reprezentowania tekstu.|
|[Platform::StringReference, klasa](../cppcx/platform-stringreference-class.md)|Umożliwia dostęp do buforów ciągu z co najmniej obciążenie kopiowania.|
|[Platform::Type, klasa](../cppcx/platform-type-class.md)|Identyfikuje typ wbudowany przez wyliczenie kategorii.|
|[Platform::ValueType, klasa](../cppcx/platform-valuetype-class.md)|Klasa bazowa dla wystąpień typów wartości.|
|[Platform::WeakReference, klasa](../cppcx/platform-weakreference-class.md)|Udostępnia słabe odwołanie do obiektów klasy referencyjnej, która zwiększa liczbę odwołań.|
|[Platform::WriteOnlyArray, klasa](../cppcx/platform-writeonlyarray-class.md)|Reprezentuje tablicę jednowymiarową tylko do zapisu, który jest używany jako parametr wejściowy w metodach, które implementują wzorzec FillArray.|
|[Platform::WrongThreadException, klasa](../cppcx/platform-wrongthreadexception-class.md)|Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu, który jest dla obiektu serwera proxy, który nie należy do komórka wątku.|

**Implementacje interfejsu**

Przestrzeń nazw platformy definiuje następujące interfejsy.

|Interface|Opis|
|---------------|-----------------|
|[Platform::IBox, interfejs](../cppcx/platform-ibox-interface.md)|Służy do przekazywania typów wartości do funkcji, której parametry o typach Platform::Object ^.|
|[Platform::IBoxArray, interfejs](../cppcx/platform-iboxarray-interface.md)|Interfejs używany do przekazywania tablic typów wartości do funkcji, której parametry o typach Platform::Array.|
|[Platform::IDisposable, interfejs](../cppcx/platform-idisposable-interface.md)|Używane, aby zwolnić niezarządzane zasoby.|

**Wyliczenia**

Przestrzeń nazw platformy ma następujące wyliczenia.

|Interface|Opis|
|---------------|-----------------|
|[Platform::CallbackContext, wyliczenie](../cppcx/platform-callbackcontext-enumeration.md)|Wyliczenie, która jest używana jako parametr konstruktora delegata. Ustala, czy wywołanie zwrotne jest skierowany, źródłowy wątku lub wątku wywołującego.|
|[Platform::TypeCode, wyliczenie](../cppcx/platform-typecode-enumeration.md)|Określa liczbowych kategorię, która reprezentuje typ wbudowany.|

**Struktury**

Przestrzeń nazw platformy ma następujące struktury.

|Struktura|Opis|
|---------------|-----------------|
|[Platform::Enum, klasa](../cppcx/platform-enum-class.md)|Reprezentuje nazwanej stałej.|
|[Platform::Guid, klasa wartości](../cppcx/platform-guid-value-class.md)|Reprezentuje identyfikator GUID.|
|[Platform::IntPtr, klasa wartości](../cppcx/platform-intptr-value-class.md)|Podpisem wskaźnik, którego rozmiar jest odpowiedni dla platformy (32-bitowy lub 64-bitowy).|
|[Platform::SizeT, klasa wartości](../cppcx/platform-sizet-value-class.md)|Typ danych bez znaku, używany do reprezentowania rozmiar obiektu.|
|[Platform::UIntPtr, klasa wartości](../cppcx/platform-uintptr-value-class.md)|Wskaźnika bez znaku, którego rozmiar jest odpowiedni dla platform (32-bitowy lub 64-bitowych).|

## <a name="see-also"></a>Zobacz też

[Platform::Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Runtime::CompilerServices, przestrzeń nazw](../cppcx/platform-runtime-compilerservices-namespace.md)<br/>
[Platform::Runtime::InteropServices, przestrzeń nazw](../cppcx/platform-runtime-interopservices-namespace.md)<br/>
[Platform::Metadata, przestrzeń nazw](../cppcx/platform-metadata-namespace.md)