---
title: Wymiana danych dla widoków rekordów (MFC Data Access) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 58bda2d9a712e38951b8201c08e5bbbe369537eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089418"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Wymiana danych dla widoków rekordów (dostęp do danych MFC)
Jeśli używasz [Dodaj klasę](../mfc/reference/adding-an-mfc-odbc-consumer.md) do mapy formantów w widoku rekordu okna dialogowego szablonu zasobów do pola zestawu rekordów, platformę zarządza wymiany danych w obu kierunkach — z zestawu rekordów do kontrolek i formanty do zestawu rekordów. Przy użyciu mechanizmu DDX oznacza, że nie trzeba napisać kod na przesyłanie danych do i z powrotem samodzielnie.  
  
 DDX dla widoków rekordów działa w połączeniu z [RFX](../data/odbc/record-field-exchange-rfx.md) dla zestawów rekordów klasy `CRecordset` (ODBC).  RFX przenosi dane między bieżącego rekordu źródła danych i elementy członkowskie danych pola obiektu zestawu rekordów. DDX przenosi dane z elementy członkowskie danych pola do formantów w formularzu. Ta kombinacja wypełnia kontrolek formularza początkowym i jako przenosi użytkownika z rekordami. Go można także cofnąć zaktualizowanych danych do zestawu rekordów, a następnie ze źródłem danych.  
  
 Na poniższej ilustracji przedstawiono relację między DDX i RFX dla widoków rekordów.  
  
 ![Okno dialogowe&#45;wymiany danych i rejestrowanie&#45;wymiana pól](../data/media/vc37xt1.gif "vc37xt1")  
Wymiana danych okna dialogowego i wymiana pól rekordów  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać więcej informacji na temat RFX, zobacz [wymiany pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)