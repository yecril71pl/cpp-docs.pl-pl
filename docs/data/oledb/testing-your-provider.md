---
title: Testowanie dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 42186d789c1b85c359b9e3e30883929a6c71ab33
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265116"
---
# <a name="testing-your-provider"></a>Testowanie dostawcy

Przed publikacją dostawcę, należy wykonać następujące testy, we wskazanej kolejności. Testy te pokazują, że funkcje dostawcy prawidłowo dla większości użytkowników potencjalnych.

1. Testowanie dostawcy przy użyciu [konsumenta](../../data/oledb/creating-an-ole-db-consumer.md) aplikacji napisanych z szablonami konsumentów OLE DB. Konsument testu powinien obejmować wszystkich obszarów funkcjonalnych w dostawcy (cały kod, który został dodany lub zmodyfikowany).

1. Testowanie dostawcy za pomocą aplikacji konsumentów napisane przy użyciu obiektów ADO. Większość deweloperów (szczególnie deweloperzy języka Visual Basic i Microsoft C#) na użytek ADO lub ADO.NET aplikacje komercyjne. Konsument testu powinien obejmować wszystkich obszarów funkcjonalnych w dostawcy. Na przykład aplikacja konsumenta ADO zobacz [przykłady kodu ADO w programie Microsoft Visual Basic](https://msdn.microsoft.com/library/ms807514.aspx).

1. Uruchom testów zgodności OLE DB (w tym testów zgodności z ADO), aby pokazać, że Twój dostawca spełnia poziom 0 standardowych dla dostawcy OLE DB. (Objaśnienia dotyczące poziom 0, wyszukaj **testów zgodności z OLE DB poziom 0** na [OLE DB przewodnik](/previous-versions/windows/desktop/ms713643). Te testy i dokumentacji skojarzone są dołączone do Visual C++ w programie Data Access SDK. Testy te ułatwiają również pokazać, że Twój dostawca działa dobrze w przypadku, gdy zagregowane przez inne [dostawców usług](../../data/oledb/ole-db-resource-pooling-and-services.md) i są szczególnie przydatne, jeśli modyfikujesz lub dodać właściwości. Aby uzyskać więcej informacji na temat testów zgodności zobacz plik Readme dla Data Access SDK, który znajduje się na jednym z dysków CD z pakietu Visual Studio.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)