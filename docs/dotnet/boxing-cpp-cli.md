---
title: Konwersja boxing (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e49c6f82099e6d7dbcfc47079d19228d7a91dc05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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