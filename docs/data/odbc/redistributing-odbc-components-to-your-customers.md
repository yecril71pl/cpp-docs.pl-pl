---
title: "Redystrybucja składników ODBC wśród klientów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 861eceef234b77b96179c51979cb7d1c0d09eeeb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redystrybucja składników ODBC wśród klientów
Jeśli funkcje programów ODBC Administrator należy dołączyć do aplikacji, należy rozproszyć użytkownikom również pliki, które uruchamiać te programy. Te pliki ODBC znajdują się w katalogu \OS\System dysku CD programu Visual C++. Plik Redistrb.wri i umowy licencyjnej, w tym samym katalogu zawierają listę plików ODBC, które można było ponownie dystrybuować.  
  
 Zajrzyj do dokumentacji wszystkich sterowników ODBC, które mają zostać wysłane. Należy określić, które biblioteki dll i inne pliki do wysłania. Należy przeczytać [Redystrybucja składników ODBC wśród klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md), które wyjaśniono, jak wykonać ponowną dystrybucję składników ODBC.  
  
 Ponadto należy dołączyć inny plik w większości przypadków. Odbccr32.dll jest z biblioteki kursorów ODBC. Ta biblioteka zawiera sterowniki poziomu 1 możliwości przewijanie do przodu i do tyłu. Udostępnia możliwość obsługi migawek. Aby uzyskać więcej informacji na temat z biblioteki kursorów ODBC, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Więcej informacji o korzystaniu z klasami baz danych ODBC można znaleźć w następujących tematach:  
  
-   [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC: Konfigurowanie źródła danych ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC: Bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)   
 [ODBC Administrator](../../data/odbc/odbc-administrator.md)