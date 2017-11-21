---
title: "Dostęp do danych za pomocą ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f243b18b2666c21a6d83eabe35ecd6ad9df5905c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-access-using-adonet-ccli"></a>Dostęp do danych za pomocą ADO.NET (C++/CLI)
ADO.NET jest interfejsu API programu .NET Framework w celu dostępu do danych i zapewnia zasilania i łatwość użycia niedopasowane przez poprzednie rozwiązania dostępu do danych. W tej sekcji opisano niektóre problemy dotyczące ADO.NET, które są unikatowe dla użytkowników programu Visual C++, takich jak przekazywanie natywnych typów.  
  
 ADO.NET działa w obszarze środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym dowolnej aplikacji, która współdziała z ADO.NET muszą również wskazywać środowiska CLR. Jednakże który oznacza, że natywnych aplikacji nie można użyć ADO.NET. Te przykłady pokazują, jak wchodzić w interakcję z bazy danych programu ADO.NET z kodu macierzystego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: kierowanie ciągów ANSI dla ADO.NET (C + +/ CLI)](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [Porady: kierowanie ciągów BSTR dla ADO.NET (C + +/ CLI)](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [Porady: kierowanie ciągów Unicode dla ADO.NET (C + +/ CLI)](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [Porady: kierowanie obiektu VARIANT dla ADO.NET (C + +/ CLI)](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [Porady: kierowanie obiektu SAFEARRAY dla ADO.NET (C + +/ CLI)](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Sekcja|Opis|  
|-------------|-----------------|  
|[ADO.NET](/dotnet/framework/data/adonet/index)|Zawiera omówienie ADO.NET, zestaw klas, które udostępniają usługi dostępu do danych dla programisty .NET.|  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Macierzysty i współdziałaniu .NET](../dotnet/native-and-dotnet-interoperability.md)