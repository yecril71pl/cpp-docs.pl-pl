---
title: Atrybuty języka C++ dla modelu COM i platformy .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 734d82a30df3e143a6f47cb1b3eca2cd778830bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214932"
---
# <a name="c-attributes-for-com-and-net"></a>Atrybuty języka C++ dla modelu COM i platformy .NET

Firma Microsoft definiuje zestaw C++ atrybutów, które upraszczają programowanie obiektów COM i .NET Framework opracowywanie środowiska uruchomieniowego języka wspólnego. Po dołączeniu atrybutów do plików źródłowych kompilator współpracuje z bibliotekami DLL dostawcy, aby wstawić kod lub zmodyfikować kod w wygenerowanych plikach obiektów. Te atrybuty ułatwiają tworzenie plików. idl, interfejsów, bibliotek typów i innych elementów COM. W zintegrowanym środowisku programistycznym (IDE) atrybuty są obsługiwane przez kreatorów i okno Właściwości.

Chociaż atrybuty eliminują niektóre ze szczegółowych kodowania potrzebnych do pisania obiektów COM, potrzebujesz tła dla [podstawowych elementów com](/windows/win32/com/the-component-object-model) , aby najlepiej z nich korzystać.

> [!NOTE]
> Jeśli szukasz C++ standardowych atrybutów, zobacz [atrybuty](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Cel atrybutów

Atrybuty zwiększają C++ się w kierunkach, które nie są obecnie dostępne bez przerywania klasycznej struktury języka. Atrybuty Zezwalaj dostawcom (oddzielnym Bibliotekom DLL) na dynamiczne zwiększanie funkcjonalności języka. Głównym celem atrybutów jest uproszczenie tworzenia składników modelu COM, a także zwiększenie poziomu produktywności dla deweloperów składnika. Atrybuty mogą być stosowane do niemal każdej C++ konstrukcji, takich jak klasy, składowe danych lub funkcje członkowskie. Poniżej przedstawiono wyróżnienie korzyści oferowanych przez tę nową technologię:

- Ujawnia znaną i prostą konwencję wywoływania.

- Używa wstawionego kodu, który, w przeciwieństwie do makr, jest rozpoznawany przez debuger.

- Umożliwia łatwe wyprowadzanie z klas bazowych bez uciążliwości szczegółów implementacji.

- Zastępuje dużą ilość kodu IDL wymaganego przez składnik COM przy użyciu kilku zwięzłych atrybutów.

Na przykład w celu zaimplementowania prostego ujścia zdarzeń dla generycznej klasy ATL można zastosować atrybut [event_receiver](event-receiver.md) do określonej klasy, takiej jak `CMyReceiver`. Atrybut `event_receiver` jest następnie kompilowany przez kompilator firmy Microsoft C++ , który wstawia odpowiedni kod do pliku obiektu.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Następnie można skonfigurować `CMyReceiver` metody `handler1` i `handler2` do obsługi zdarzeń (przy użyciu funkcji wewnętrznej [__hook](../../cpp/hook.md)) ze źródła zdarzeń, które można utworzyć przy użyciu [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Podstawowa mechanika atrybutów

Istnieją trzy sposoby wstawiania atrybutów do projektu. Najpierw można wstawić je ręcznie do kodu źródłowego. Następnie można wstawić je za pomocą siatki właściwości obiektu w projekcie. Na koniec można je wstawić przy użyciu różnych kreatorów. Aby uzyskać więcej informacji na temat korzystania z okna **Właściwości** i różnych kreatorów, zobacz [Visual Studio C++projects- ](../../build/creating-and-managing-visual-cpp-projects.md).

Tak jak wcześniej, podczas kompilowania projektu kompilator analizuje każdy C++ plik źródłowy, generując plik obiektu. Jeśli jednak kompilator napotka atrybut, jest on analizowany i syntaktycznie zweryfikowany. Następnie kompilator dynamicznie wywołuje dostawcę atrybutów, aby wstawić kod lub wprowadzić inne modyfikacje w czasie kompilacji. Implementacja dostawcy różni się w zależności od typu atrybutu. Na przykład atrybuty związane z ATL są implementowane przez Atlprov. dll.

Na poniższej ilustracji przedstawiono relacje między kompilatorem a dostawcą atrybutów.

![Komunikacja atrybutów składników](../media/vccompattrcomm.gif "Komunikacja atrybutów składników")

> [!NOTE]
> Użycie atrybutów nie powoduje zmiany zawartości pliku źródłowego. Jedyny wygenerowany kod atrybutu jest widoczny podczas debugowania sesji. Ponadto dla każdego pliku źródłowego w projekcie można wygenerować plik tekstowy, który wyświetla wyniki podstawienia atrybutu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [/FX (Scalanie wstrzykniętego kodu)](../../build/reference/fx-merge-injected-code.md) i [debugowanie wstrzykniętego kodu](/visualstudio/debugger/how-to-debug-injected-code).

Podobnie jak C++ większość konstrukcji, atrybuty mają zestaw cech, który definiuje ich prawidłowe użycie. Jest to nazywane kontekstem atrybutu i jest rozwoływany w tabeli kontekstowej atrybutu dla każdego tematu odwołania do atrybutu. Na przykład atrybut [coclass](coclass.md) może być stosowany tylko do istniejącej klasy lub struktury, w przeciwieństwie do atrybutu [cpp_quote](cpp-quote.md) , który można wstawić w dowolnym miejscu w pliku C++ źródłowym.

## <a name="building-an-attributed-program"></a>Kompilowanie programu opartego na atrybutach

Po umieszczeniu atrybutów wizualnych C++ w kodzie źródłowym możesz chcieć, aby kompilator firmy Microsoft C++ generował plik biblioteki typów i IDL. Poniższe opcje konsolidatora ułatwiają tworzenie plików TLB i IDL:

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Niektóre projekty zawierają wiele niezależnych plików. idl. Są one używane do tworzenia dwóch lub więcej plików. tlb i opcjonalnie powiązania ich z blokiem zasobów. Ten scenariusz nie jest obecnie obsługiwany w programie C++Visual.

Ponadto, konsolidator wizualny C++ będzie wyprowadzał wszystkie informacje o atrybutach IDL do pojedynczego pliku MIDL. Nie będzie można generować dwóch bibliotek typów z pojedynczego projektu.

## <a name="attribute-contexts"></a><a name="contexts"></a>Konteksty atrybutu

C++atrybuty można opisać przy użyciu czterech podstawowych pól: cel, do którego można zastosować (**dotyczy**), jeśli są powtarzalne lub nie (**powtarzalne**), wymagana obecność innych atrybutów (**wymaganych atrybutów**) i niezgodności z innymi atrybutami (**nieprawidłowe atrybuty**). Te pola są wymienione w tabeli towarzyszącej w temacie odwołania do poszczególnych atrybutów. Każde z tych pól zostało opisane poniżej.

### <a name="applies-to"></a>Dotyczy

To pole opisuje różne C++ elementy języka, które są dozwolonymi celami dla określonego atrybutu. Na przykład, jeśli atrybut określa "Class" w polu **dotyczy** , oznacza to, że atrybut może być stosowany tylko do klasy prawnej C++ . Jeśli atrybut jest stosowany do funkcji składowej klasy, wynikiem może być błąd składniowy.

Aby uzyskać więcej informacji, zobacz [atrybuty według użycia](attributes-by-usage.md).

### <a name="repeatable"></a>Powtarzalne

To pole określa, czy atrybut może być wielokrotnie stosowany do tego samego obiektu docelowego. Większość atrybutów nie jest powtarzana.

### <a name="required-attributes"></a>Wymagane atrybuty

To pole zawiera listę innych atrybutów, które muszą być obecne (to jest stosowane do tego samego obiektu docelowego), aby określony atrybut działał prawidłowo. Dla atrybutu nie można mieć żadnych wpisów dla tego pola.

### <a name="invalid-attributes"></a>Nieprawidłowe atrybuty

To pole zawiera listę innych atrybutów, które są niezgodne z określonym atrybutem. Dla atrybutu nie można mieć żadnych wpisów dla tego pola.

## <a name="in-this-section"></a>W tej sekcji

[Programowanie oparte na atrybutach —najczęściej zadawane pytania](attribute-programming-faq.md)<br/>
[Atrybuty według grup](attributes-by-group.md)<br/>
[Atrybuty w zależności od zastosowania](attributes-by-usage.md)<br/>
[Alfabetyczny spis atrybutów](attributes-alphabetical-reference.md)
