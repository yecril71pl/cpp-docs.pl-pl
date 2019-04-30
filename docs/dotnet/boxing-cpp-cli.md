---
title: Konwersja boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 3f756eaef59c24ca5b82c485bd8352dffe9fb1db
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345769"
---
# <a name="boxing-ccli"></a>Konwersja boxing (C++/CLI)

OPAKOWYWANIE to proces konwersji typu wartości do typu `object` lub dowolny typ interfejsu, który jest implementowany przez typ wartości. Środowisko uruchomieniowe języka wspólnego (CLR) pola typu wartości, otacza wartość `System.Object` i zapisuje go w zarządzanym stosie. Rozpakowywanie wyodrębnia typ wartości z obiektu. OPAKOWYWANIE jest niejawne; Rozpakowywanie jest jawne.

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)|Opisuje sposób jawne żądanie konwersji boxing na zmiennej.|
|[Instrukcje: używanie funkcji gcnew do tworzenia typów wartości i korzystanie z niejawnej konwersji boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Ilustruje sposób używania `gcnew` w celu utworzenia typu wartości spakowanej, który można umieścić na stosie zarządzanym, zebranych elementów bezużytecznych.|
|[Instrukcje: rozpakowywanie](../dotnet/how-to-unbox.md)|Pokazuje, jak rozpakowania i zmodyfikuj wartości.|
|[Konwersje standardowe i niejawne konwersje boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Pokazuje, że konwersja standardowa jest wybierany przez kompilator za pośrednictwem konwersji, która wymaga opakowania.|
|[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Artykuł najwyższego poziomu dla programowania .NET w dokumentacji języka Visual C++.|