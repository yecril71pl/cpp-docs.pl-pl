---
title: Konwersja boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: df0e220c4f744e78aa5bedce4f956b726f524ff4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208838"
---
# <a name="boxing-ccli"></a>Konwersja boxing (C++/CLI)

Opakowanie to proces konwersji typu wartości na typ `object` lub do dowolnego typu interfejsu, który jest implementowany przez typ wartości. Gdy typ wartości pola środowiska uruchomieniowego języka wspólnego (CLR), zawija wartość w `System.Object` i zapisuje ją na zarządzanym stosie. Rozpakowywanie wyodrębnia typ wartości z obiektu. Opakowanie jest niejawne; Rozpakowywanie jest jawne.

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)|Opisuje, jak jawnie zażądać opakowania na zmiennej.|
|[Instrukcje: używanie funkcji gcnew do tworzenia typów wartości i korzystanie z niejawnej konwersji boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Pokazuje, w jaki sposób używać `gcnew` do tworzenia opakowanego typu wartości, który może być umieszczany na zarządzanej stercie.|
|[Instrukcje: rozpakowywanie](../dotnet/how-to-unbox.md)|Pokazuje, jak Unbox i modyfikować wartość.|
|[Konwersje standardowe i niejawne konwersje boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Pokazuje, że konwersja standardowa jest wybierana przez kompilator nad konwersją wymagającą opakowania.|
|[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Artykuł najwyższego poziomu dla programowania .NET w dokumentacji wizualnej C++ .|
