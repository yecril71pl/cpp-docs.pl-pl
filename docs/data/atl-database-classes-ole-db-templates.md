---
title: Klasy baz danych ATL (szablony OLE DB) | Dokumentacja firmy Microsoft
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
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca7607c037cdb1f6a42a2267d64ef274d1041cb2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="atl-database-classes-ole-db-templates"></a>Klasy baz danych ATL (Szablony OLE DB)
Firma Microsoft udostępnia kilka implementacje OLE DB, zestaw interfejsów modelu COM, które umożliwiają uniform dostęp do danych w formatach i informacje o różnych źródeł.  OLE DB oficjalnie jest przestarzały; Niniejsza dokumentacja jest dla deweloperów, którzy są utrzymywanie starszej wersji kodu. Nowe aplikacje powinny używać ODBC do łączenia się ze źródłami danych SQL.
  
 Szablony OLE DB są szablonów języka C++ w ATL, które ułatwiają korzystanie zapewniając klas implementujących wiele interfejsów OLE DB często używanych technologii bazy danych OLE DB.  
  
 Ta biblioteka szablonów zawiera dwa składniki:  
  
-   [Szablony konsumentów OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) używaną do zaimplementowania w aplikacji OLE DB klienta (użytkownika).  
  
-   [Szablony dostawców OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) używaną do zaimplementowania OLE DB aplikacji serwera (dostawcy).  
  
 Ponadto [atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md) zapewnić wygodny sposób utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu, w oparciu o szablony konsumentów OLE DB, aby utworzyć pracy konsumentów OLE DB.  
  
 Należy pamiętać, że biblioteka MFC zawiera jedną klasę [coledbrecordview —](../mfc/reference/coledbrecordview-class.md), który wyświetla w formantach rekordów bazy danych. Widok jest widokiem formularza bezpośrednio podłączone do `CRowset` obiektu i są wyświetlane pola `CRowset` obiektu w formantach szablonu okna dialogowego.  
  
 Aby uzyskać więcej informacji, zobacz [OLE DB programowania](../data/oledb/ole-db-programming.md) i [OLE DB przewodnik](http://go.microsoft.com/fwlink/p/?linkid=121548).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Tworzenie dostawcy OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Dokumentacja szablonów OLE DB Provider](../data/oledb/ole-db-provider-templates-reference.md)   
 [Przykłady szablonów OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)