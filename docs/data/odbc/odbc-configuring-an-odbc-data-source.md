---
title: "ODBC: Konfigurowanie źródła danych ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e347683a079227226513ce82f9623860e826228
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC: konfigurowanie źródła danych ODBC
Aby użyć [źródła danych](../../data/odbc/data-source-odbc.md) z aplikacją korzystasz, należy użyć konta administratora ODBC ją skonfigurować. ODBC Administrator przechowuje informacje o dostępnych źródeł danych i parametry połączenia w rejestrze systemu Windows. Administrator ODBC używana do dodawania, modyfikowania i usuwania źródeł danych w **źródeł danych** okno dialogowe i do dodawania i usuwania sterowników ODBC.  
  
> [!NOTE]
>  Te informacje dotyczą używania klas MFC obiekt DAO (Data Access) dla dostępu ODBC i używania klas MFC ODBC.  
  
 ODBC Administrator jest automatycznie instalowany z obsługi bazy danych biblioteki Microsoft Foundation Classes (MFC). Aby uzyskać więcej informacji na temat programu ODBC Administrator, zobacz [ODBC Administrator](../../data/odbc/odbc-administrator.md) i system ODBC API Pomoc online.  
  
 Aby uzyskać informacje dotyczące pisania aplikacji baz danych MFC ODBC do instalacji i administrowania programy[48 Uwaga techniczna](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)   
 [ODBC: Bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)