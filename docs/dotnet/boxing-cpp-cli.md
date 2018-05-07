---
title: Konwersja boxing (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3b9898b4a640d2f3aa4e38ceb621521ffb301fed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="boxing-ccli"></a>Konwersja boxing (C++/CLI)
Opakowanie jest proces konwersji typu wartości na typ `object` lub do dowolnego typu interfejsu, który jest implementowany przez typ wartości. Jeśli środowisko uruchomieniowe języka wspólnego (CLR) pola typu wartości, jest zawijany wartość w `System.Object` i zapisuje go na stercie zarządzanej. Rozpakowywanie wyodrębnia typ wartości z obiektu. Opakowanie jest niejawne; Rozpakowywanie jest jawne.  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)|Opisuje sposób jawne żądanie konwersji boxing w zmiennej.|  
|[Instrukcje: używanie funkcji gcnew do tworzenia typów wartości i korzystanie z niejawnej konwersji boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Przedstawia sposób użycia `gcnew` do utworzenia typu wartości spakowanej, który można umieścić na stercie zarządzanej, zbierane w pamięci.|  
|[Instrukcje: rozpakowywanie](../dotnet/how-to-unbox.md)|Przedstawia sposób unbox — i zmodyfikuj wartość.|  
|[Konwersje standardowe i niejawne konwersje boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Pokazuje, czy konwersja standardowa jest wybierany przez kompilator za pośrednictwem konwersji, która wymaga opakowania.|  
|[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Artykuł najwyższego poziomu programowania .NET w dokumentacji Visual C++.|