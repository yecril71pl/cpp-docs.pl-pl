---
title: "Dostęp do danych za pomocą ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fb7d184ebdb537c02b79a412d69a4bdcaabde424
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-access-using-adonet-ccli"></a>Dostęp do danych za pomocą ADO.NET (C++/CLI)
ADO.NET jest interfejsu API programu .NET Framework w celu dostępu do danych i zapewnia zasilania i łatwość użycia niedopasowane przez poprzednie rozwiązania dostępu do danych. W tej sekcji opisano niektóre problemy dotyczące ADO.NET, które są unikatowe dla użytkowników programu Visual C++, takich jak przekazywanie natywnych typów.  
  
 ADO.NET działa w obszarze środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym dowolnej aplikacji, która współdziała z ADO.NET muszą również wskazywać środowiska CLR. Jednakże który oznacza, że natywnych aplikacji nie można użyć ADO.NET. Te przykłady pokazują, jak wchodzić w interakcję z bazy danych programu ADO.NET z kodu macierzystego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: przeprowadzanie marshalingu ciągów ANSI dla ADO.NET (C++/CLI)](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [Instrukcje: przeprowadzanie marshalingu ciągów BSTR dla ADO.NET (C++/CLI)](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [Instrukcje: przeprowadzanie marshalingu ciągów Unicode dla ADO.NET (C++/CLI)](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [Instrukcje: przeprowadzanie marshalingu obiektu VARIANT dla ADO.NET (C++/CLI)](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [Instrukcje: przeprowadzanie marshalingu obiektu SAFEARRAY dla ADO.NET (C++/CLI)](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Sekcja|Opis|  
|-------------|-----------------|  
|[ADO.NET](/dotnet/framework/data/adonet/index)|Zawiera omówienie ADO.NET, zestaw klas, które udostępniają usługi dostępu do danych dla programisty .NET.|  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)