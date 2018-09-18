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
ms.openlocfilehash: d175216fedb2e6a9139d970fc7696672576f7423
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042900"
---
# <a name="testing-your-provider"></a>Testowanie dostawcy

Przed publikacją dostawcę, należy wykonać następujące testy we wskazanej kolejności. Te testy upewnij się, że funkcje dostawcy prawidłowo dla większości użytkowników potencjalnych.  
  
1. Testowanie dostawcy przy użyciu [konsumenta](../../data/oledb/creating-an-ole-db-consumer.md) aplikacji napisanych z szablonami konsumentów OLE DB. Konsument testu powinien obejmować wszystkich obszarów funkcjonalnych w dostawcy (cały kod, który zostanie dodany lub zmodyfikowany).  
  
1. Testowanie dostawcy za pomocą aplikacji konsumentów napisane przy użyciu obiektów ADO. Większość deweloperów (szczególnie deweloperzy języka Visual Basic i Microsoft C#) na użytek ADO lub ADO.NET aplikacje komercyjne. Konsument testu powinien obejmować wszystkich obszarów funkcjonalnych w dostawcy. Na przykład aplikacja konsumenta ADO zobacz [przykłady kodu ADO w programie Microsoft Visual Basic](https://msdn.microsoft.com/library/ms807514.aspx).  
  
1. Uruchom testów zgodności OLE DB (w tym testów zgodności z ADO), aby upewnić się, że Twój dostawca spełnia poziom 0 standardowych dla dostawcy OLE DB. (Objaśnienia dotyczące poziom 0, wyszukaj "OLE DB poziom 0 testów zgodności" w [OLE DB przewodnik](/previous-versions/windows/desktop/ms713643\(v=vs.85\)). Te testy i dokumentacji skojarzone są dołączone do Visual C++ w programie Data Access SDK. Testy te ułatwiają również upewnić się, że Twój dostawca działa dobrze w przypadku, gdy zagregowane przez inne [dostawców usług](../../data/oledb/ole-db-resource-pooling-and-services.md) i są szczególnie przydatne, jeśli modyfikujesz lub dodać właściwości. Aby uzyskać więcej informacji na temat testów zgodności zobacz plik Readme dla Data Access SDK, który znajduje się na jednym z dysków CD z pakietu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)