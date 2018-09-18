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
ms.openlocfilehash: 8dcefa3068cb27514671094194ba590e99402b05
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021100"
---
# <a name="atl-database-classes-ole-db-templates"></a>Klasy baz danych ATL (Szablony OLE DB)

Firma Microsoft udostępnia kilka implementacji OLE DB, zbiór interfejsów COM, które udostępniają jednolity dostęp do danych z różnymi źródłami informacji i formatów.  OLE DB oficjalnie jest przestarzała; Ta dokumentacja jest dla deweloperów, którzy są obsługi starszego kodu. Nowe aplikacje powinny używać ODBC do łączenia ze źródłami danych SQL.
  
Szablony OLE DB są szablonami języka C++ w ATL, które ułatwiają korzystanie, zapewniając klas implementujących wiele powszechnie używanych interfejsów OLE DB technologii baz danych OLE DB.  
  
Ta biblioteka szablon zawiera dwie części:  
  
- [Szablony konsumentów OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) używaną do zaimplementowania aplikacja kliencka (użytkownik) OLE DB.  
  
- [Szablony dostawców OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) używany do implementowania aplikacji serwera (dostawca) OLE DB.  
  
Ponadto [atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md) zapewniają wygodny sposób, aby utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu, w oparciu o szablony konsumentów OLE DB, aby utworzyć konsumentów OLE DB pracy.  
  
Należy pamiętać, że biblioteka MFC zawiera jedną klasę [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), który wyświetla rekordy bazy danych w kontrolkach. Widok jest podłączone bezpośrednio do widoku formularza `CRowset` obiektu, a następnie wyświetla pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego.  
  
Aby uzyskać więcej informacji, zobacz [OLE DB programowania](../data/oledb/ole-db-programming.md) i [OLE DB przewodnik](/previous-versions/windows/desktop/ms713643\(v=vs.85\)).  
  
## <a name="see-also"></a>Zobacz też  

[Tworzenie konsumenta OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Tworzenie dostawcy OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Szablony dostawców OLE DB — dokumentacja](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Przykłady szablonów OLE DB](https://github.com/Microsoft/VCSamples)