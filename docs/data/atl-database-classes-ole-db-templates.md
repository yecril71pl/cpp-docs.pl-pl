---
title: Klasy baz danych ATL (szablony OLE DB) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 91cd06ea1d8ff697da6c4959fff34fdc3798dcfd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218991"
---
# <a name="atl-database-classes-ole-db-templates"></a>Klasy baz danych ATL (Szablony OLE DB)
Firma Microsoft udostępnia kilka implementacji OLE DB, zbiór interfejsów COM, które udostępniają jednolity dostęp do danych z różnymi źródłami informacji i formatów.  OLE DB oficjalnie jest przestarzała; Ta dokumentacja jest dla deweloperów, którzy są obsługi starszego kodu. Nowe aplikacje powinny używać ODBC do łączenia ze źródłami danych SQL.
  
 Szablony OLE DB są szablonami języka C++ w ATL, które ułatwiają korzystanie, zapewniając klas implementujących wiele powszechnie używanych interfejsów OLE DB technologii baz danych OLE DB.  
  
 Ta biblioteka szablon zawiera dwie części:  
  
-   [Szablony konsumentów OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) używaną do zaimplementowania aplikacja kliencka (użytkownik) OLE DB.  
  
-   [Szablony dostawców OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) używany do implementowania aplikacji serwera (dostawca) OLE DB.  
  
 Ponadto [atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md) zapewniają wygodny sposób, aby utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu, w oparciu o szablony konsumentów OLE DB, aby utworzyć konsumentów OLE DB pracy.  
  
 Należy pamiętać, że biblioteka MFC zawiera jedną klasę [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), który wyświetla rekordy bazy danych w kontrolkach. Widok jest podłączone bezpośrednio do widoku formularza `CRowset` obiektu, a następnie wyświetla pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego.  
  
 Aby uzyskać więcej informacji, zobacz [OLE DB programowania](../data/oledb/ole-db-programming.md) i [OLE DB przewodnik](http://go.microsoft.com/fwlink/p/?linkid=121548).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Tworzenie dostawcy OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB — Kompendium szablonów konsumentów](../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB Provider szablony — dokumentacja](../data/oledb/ole-db-provider-templates-reference.md)   
 [Przykłady szablonów OLE DB](https://msdn.microsoft.com/08958863-0b5f-41ad-ae99-fca7440c553c)