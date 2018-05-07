---
title: Testowanie dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c35b1391e5b8cbfb073255b3680b0376d19ae040
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="testing-your-provider"></a>Testowanie dostawcy
Przed udostępnieniem dostawcę, należy wykonać następujące testy w kolejności wskazanej. Te testy upewnij się, że funkcje dostawcy prawidłowo dla większości użytkowników potencjalnych.  
  
1.  Testowanie dostawcy przy użyciu [konsumenta](../../data/oledb/creating-an-ole-db-consumer.md) Aplikacja napisana z szablonami konsumentów OLE DB. Konsument testu powinno obejmować wszystkich obszarów funkcjonalnych dostawcy (całego kodu, które zostały dodane lub zmodyfikowane).  
  
2.  Testowanie dostawcy przy użyciu aplikacji konsumenta napisany za pomocą ADO. Większość deweloperów (szczególnie deweloperów języka Visual Basic i Microsoft C#) Użyj ADO lub ADO.NET dla aplikacji klienta. Konsument testu powinno obejmować wszystkich obszarów funkcjonalnych dostawcy. Na przykład aplikacja konsumenta ADO zobacz [ADO przykłady kodu w języku Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Uruchom testy zgodności OLE DB (w tym testy zgodności ADO), aby upewnić się, że Twój dostawca spełnia poziom 0 standardowe dla dostawcy OLE DB. (Aby uzyskać informacje o poziomie 0, wyszukaj "OLE DB poziom 0 testów zgodności" w [OLE DB przewodnik](http://go.microsoft.com/fwlink/p/?linkid=121548). Te testy i skojarzone dokumentacji są dołączone do programu Visual C++ w zestawie SDK dostępu do danych. Te testy również ułatwić zapewnienie, że dostawcy działa również w przypadku, gdy agregowana przez inne [dostawców usług](../../data/oledb/ole-db-resource-pooling-and-services.md) i są szczególnie przydatne w przypadku modyfikowanie lub dodawanie właściwości. Aby uzyskać więcej informacji dotyczących testów zgodności zobacz plik Readme dla zestawu SDK dostępu do danych, który znajduje się na jednym z dysków CD programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)