---
title: Redystrybucja składników ODBC wśród klientów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0427228b8fb3e852cf1d9ee66a10c9290b860b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090227"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redystrybucja składników ODBC wśród klientów
Jeśli funkcje programów ODBC Administrator należy dołączyć do aplikacji, należy rozproszyć użytkownikom również pliki, które uruchamiać te programy. Te pliki ODBC znajdują się w katalogu \OS\System dysku CD programu Visual C++. Plik Redistrb.wri i umowy licencyjnej, w tym samym katalogu zawierają listę plików ODBC, które można było ponownie dystrybuować.  
  
 Zajrzyj do dokumentacji wszystkich sterowników ODBC, które mają zostać wysłane. Należy określić, które biblioteki dll i inne pliki do wysłania. Należy przeczytać [Redystrybucja składników ODBC wśród klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md), które wyjaśniono, jak wykonać ponowną dystrybucję składników ODBC.  
  
 Ponadto należy dołączyć inny plik w większości przypadków. Odbccr32.dll jest z biblioteki kursorów ODBC. Ta biblioteka zawiera sterowniki poziomu 1 możliwości przewijanie do przodu i do tyłu. Udostępnia możliwość obsługi migawek. Aby uzyskać więcej informacji na temat z biblioteki kursorów ODBC, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Więcej informacji o korzystaniu z klasami baz danych ODBC można znaleźć w następujących tematach:  
  
-   [ODBC: biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC: konfigurowanie źródła danych ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC: bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)   
 [Administrator ODBC](../../data/odbc/odbc-administrator.md)