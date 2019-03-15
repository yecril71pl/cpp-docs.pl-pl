---
title: Atrybuty C++ dla modelu COM i .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: f9d339860e9d2bdb8d66f6b7f8f49d3993b2d5cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820744"
---
# <a name="c-attributes-for-com-and-net"></a>Atrybuty C++ dla modelu COM i .NET

Firma Microsoft definiuje zestaw atrybutów języka C++, które upraszczają programowanie COM i .NET Framework — programowanie środowiska uruchomieniowego języka wspólnego. Gdy atrybuty zostaną umieszczone w plikach źródłowych, kompilator będzie współpracuje z dostawcą biblioteki dll, Wstaw kod lub zmodyfikować kod w plikach obiektowych wygenerowany. Te atrybuty pomocy w przypadku tworzenia plików .idl, interfejsy, bibliotek typów i innych elementów modelu COM. W zintegrowanego środowiska programistycznego (IDE) atrybutów są obsługiwane przez kreatory i okna właściwości.

Gdy atrybuty wyeliminować niektóre szczegółowe kodowanie, wymagane do zapisywania obiektów COM, potrzebujesz tła w [podstawy COM](/windows/desktop/com/the-component-object-model) najlepiej je wykorzystać.

> [!NOTE]
> Jeśli szukasz atrybuty standard C++, zobacz [atrybuty](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Cel atrybutów

Atrybuty rozszerzenia C++ w kierunkach nie jest obecnie możliwe bez przerywania klasycznej struktury języka. Atrybuty zezwalać na dostawców (oddzielne biblioteki dll) do rozszerzenia funkcji języka dynamicznie. Podstawowym celem atrybutów jest uproszczenie tworzenia składników modelu COM, oprócz zwiększenie poziomu wydajności dla deweloperów składników. Atrybuty mogą być stosowane do niemal C++ konstrukcji, takich jak klasy, elementy członkowskie danych lub elementów członkowskich. Wyróżnienie korzyści zapewniane przez nowej technologii jest następująca:

- Opisuje dobrze znanych i proste konwencji wywoływania.

- Zastosowań wstawiony kod, który w przeciwieństwie do makra, rozpoznawanym przez debuger.

- Umożliwia łatwe tworzenie wartości pochodnych z klas bazowych bez szczegółów implementacji uciążliwe.

- Zastępuje dużą ilość kodu języka IDL wymagane przez składnik COM za pomocą kilku atrybutów zwięzły.

Na przykład, aby zaimplementować obiekt sink zdarzenia prostego ogólne klasy ATL, należy zastosować [event_receiver](event-receiver.md) atrybutu do określonej klasy, takie jak `CMyReceiver`. `event_receiver` Atrybutu są następnie kompilowane przez kompilator Visual C++, który wstawia prawidłowego kodu do pliku obiektu.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Następnie można skonfigurować `CMyReceiver` metody `handler1` i `handler2` do obsługi zdarzeń (przy użyciu wewnętrznej funkcji [__hook](../../cpp/hook.md)) ze źródła zdarzeń, który można utworzyć przy użyciu [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Podstawowa mechanika atrybutów

Istnieją trzy sposoby, aby wstawić atrybuty do projektu. Po pierwsze można wstawić je ręcznie w kodzie źródłowym. Po drugie można wstawić je przy użyciu siatki właściwości obiektu w projekcie. Na koniec można wstawić je przy użyciu różnych kreatorów. Aby uzyskać więcej informacji na temat korzystania z **właściwości** okna i różne kreatory, zobacz [tworzenie i zarządzanie projekty języka Visual C++](../../build/creating-and-managing-visual-cpp-projects.md).

Jako wcześniej, gdy projekt jest kompilowany, w którym kompilator analizuje każdego pliku źródłowego języka C++, tworzenie pliku obiektu. Jednak gdy kompilator napotka atrybutu, jest analizowany i składniowo zweryfikowane. Kompilator dynamicznie wywołuje dostawcę atrybutu Wstaw kod lub wprowadzić inne zmiany w czasie kompilacji. Implementacja dostawcy różni się w zależności od typu atrybutu. Na przykład związane z ATL atrybuty są implementowane przez Atlprov.dll.

Na poniższym rysunku pokazano relację między kompilatora i dostawcy atrybutu.

![Atrybut komunikacji](../media/vccompattrcomm.gif "komunikacji atrybutu")

> [!NOTE]
> Użycie atrybutu nie zmienia zawartość pliku źródłowego. Jedyną sytuacją, w których atrybut wygenerowanego kodu jest widoczny jest podczas sesji debugowania. Ponadto dla każdego pliku źródłowego w projekcie można wygenerować plik tekstowy, który wyświetla wyniki podstawienia atrybutu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [/Fx (Scal wprowadzony kod)](../../build/reference/fx-merge-injected-code.md) i [debugowania kodu wprowadzony](/visualstudio/debugger/how-to-debug-injected-code).

Podobnie jak większość konstrukcji języka C++ atrybuty mają zestaw właściwości, który definiuje ich prawidłowego użycia. To jest określany jako kontekst atrybutu i został rozwiązany w tabeli kontekstu atrybutów dla każdego atrybutu odwołanie do tematu. Na przykład [coclass](coclass.md) atrybut tylko można stosować do istniejącej klasy lub struktury, w przeciwieństwie do [cpp_quote —](cpp-quote.md) atrybut, który można wstawić w dowolnym miejscu w obrębie pliku źródłowego języka C++.

## <a name="building-an-attributed-program"></a>Kompilowanie programu opartego na atrybutach

Po atrybuty Visual C++ są umieszczane w kodzie źródłowym, może być kompilator języka Visual C++, aby wygenerować plik biblioteki i .idl typu dla Ciebie. Konsolidator następujące opcje pomagają tworzyć plików .tlb i .idl:

- [/ IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/ IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/ TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Niektóre projekty zawierają wiele plików .idl niezależne. Są one używane do utworzenia dwóch lub więcej plików .tlb i opcjonalnie powiązać je w bloku zasobów. W tym scenariuszu nie jest obecnie obsługiwane w programie Visual C++.

Ponadto konsolidator Visual C++ zwróci wszystkie informacje związane z IDL atrybut do jednego pliku MIDL. Będzie sposób generowania dwie biblioteki typów z pojedynczego projektu.

## <a name="contexts"></a> Konteksty atrybutu

Atrybuty C++ można opisać za pomocą cztery pola podstawowe: element docelowy, mogą być stosowane do (**dotyczy**), jeśli są one powtarzalne, czy nie (**Repeatable**), wymagane obecność innych atrybutów ( **Atrybuty wymagane**) i niezgodności z innymi atrybutami (**nieprawidłowe atrybuty**). Te pola są wymienione w towarzyszącej mu tabeli, w artykule dotyczącym każdego atrybutu. Poniżej opisano każde z tych pól.

### <a name="applies-to"></a>Dotyczy:

To pole zawiera opis różnych elementów języka C++, które prawne elementów docelowych dla określonego atrybutu. Na przykład jeśli atrybut "class" Określa **dotyczy** pola, oznacza to, że ten atrybut można dotyczą wyłącznie prawne klasy języka C++. Jeśli ten atrybut jest stosowany do funkcji składowej klasy, spowoduje błąd składni.

Aby uzyskać więcej informacji, zobacz [atrybuty w zależności od użycia](attributes-by-usage.md).

### <a name="repeatable"></a>Powtarzalne

To pole określa, czy można wielokrotnie zastosować atrybutu, do tej samej wartości docelowej. Większość atrybutów nie są powtarzalne.

### <a name="required-attributes"></a>Wymaganych atrybutów

To pole zawiera inne atrybuty, które muszą być obecne (co oznacza, że są stosowane do tej samej wartości docelowej) dla określonego atrybutu działać prawidłowo. Jest nietypowy dla atrybutu powoduje, że wszystkie wpisy dla tego pola.

### <a name="invalid-attributes"></a>Nieprawidłowe atrybuty

To pole zawiera atrybuty, które nie są zgodne z określonego atrybutu. Jest nietypowy dla atrybutu powoduje, że wszystkie wpisy dla tego pola.

## <a name="in-this-section"></a>W tej sekcji

[Programowanie oparte na atrybutach —najczęściej zadawane pytania](attribute-programming-faq.md)<br/>
[Atrybuty według grup](attributes-by-group.md)<br/>
[Atrybuty w zależności od zastosowania](attributes-by-usage.md)<br/>
[Alfabetyczny spis atrybutów](attributes-alphabetical-reference.md)