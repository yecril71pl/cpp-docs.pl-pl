---
title: Konwersja boxing (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a103f03b667122e16964c8cd0bb34774a6cc9cda
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="boxing-ccli"></a>Konwersja boxing (C++/CLI)
Opakowanie jest proces konwersji typu wartości na typ `object` lub do dowolnego typu interfejsu, który jest implementowany przez typ wartości. Jeśli środowisko uruchomieniowe języka wspólnego (CLR) pola typu wartości, jest zawijany wartość w `System.Object` i zapisuje go na stercie zarządzanej. Rozpakowywanie wyodrębnia typ wartości z obiektu. Opakowanie jest niejawne; Rozpakowywanie jest jawne.  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: jawne żądanie konwersji Boxing](../dotnet/how-to-explicitly-request-boxing.md)|Opisuje sposób jawne żądanie konwersji boxing w zmiennej.|  
|[Porady: używanie funkcji gcnew do tworzenia typów wartości i użyj niejawnej konwersji Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Przedstawia sposób użycia `gcnew` do utworzenia typu wartości spakowanej, który można umieścić na stercie zarządzanej, zbierane w pamięci.|  
|[Porady: unbox —](../dotnet/how-to-unbox.md)|Przedstawia sposób unbox — i zmodyfikuj wartość.|  
|[Konwersje standardowe i niejawnej konwersji Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Pokazuje, czy konwersja standardowa jest wybierany przez kompilator za pośrednictwem konwersji, która wymaga opakowania.|  
|[.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Artykuł najwyższego poziomu programowania .NET w dokumentacji Visual C++.|