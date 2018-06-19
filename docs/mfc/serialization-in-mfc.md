---
title: Serializacja w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd5cf36722dd1ed6ea96dd839bd0935d78df0b32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381026"
---
# <a name="serialization-in-mfc"></a>Serializacja w MFC
W tym artykule opisano mechanizmu serializacji podane w Microsoft Foundation Class biblioteki (MFC) umożliwiające obiektów utrwalany między uruchamia programu.  
  
 Serializacja jest proces zapisywania lub odczytywania obiektu do lub z nośnika magazynu trwałego, takich jak pliku na dysku. Serializacja jest idealne rozwiązanie w przypadku sytuacji, w których jest potrzebne do zarządzania stanem dane strukturalne (takie jak C++ klasy lub struktury), podczas lub po zakończeniu wykonywania programu. Za pomocą serializacji obiektów dostarczanych przez MFC umożliwia to zostać przeprowadzone w sposób standardowy i spójny, co uwalnia użytkownika z konieczności ręcznego wykonywania operacji na plikach.  
  
 MFC udostępnia wbudowaną obsługę serializacji w klasie `CObject`. W związku z tym wszystkich klas pochodnych `CObject` mogą wykorzystać `CObject`przez Protokół serializacji.  
  
 Zgodnie z podstawową koncepcją serializacji to, że obiektu powinien mieć możliwość zapisywania swojego bieżącego stanu zwykle wskazywany przez wartość jego zmienne Członkowskie do magazynu trwałego. Później obiekt można ponownie utworzyć za odczytywanie lub deserializacji stan obiektu z magazynu. Serializacja obsługuje wszystkie szczegóły obiektu wskaźników i cykliczne odwołania do obiektów, które są używane podczas szeregowania obiektu. Kluczowym elementem jest odpowiedzialny za odczytywanie i Zapisywanie stanu własnych samego obiektu. W związku z tym dla klasy jako możliwy do serializacji, musi on implementować operacji podstawowe serializacji. Jak pokazano w grupie serializacji artykułów, jest łatwo dodać tę funkcję do klasy.  
  
 MFC używa obiektu `CArchive` klasy jako pośrednik między obiektem do serializacji i nośniku magazynowania. Ten obiekt jest skojarzony z zawsze `CFile` obiektu, z którego uzyska informacje niezbędne do serializacji, łącznie z nazwą pliku i określa, czy Żądana operacja jest do odczytu lub zapisu. Można użyć obiektu, który wykonuje operacje serializacji `CArchive` obiektu niezależnie rodzaj nośnika magazynowania.  
  
 A `CArchive` obiekt używa przeciążone wstawiania (**<\<**) i wyodrębniania (**>>**) operatory przeprowadzić zapisywanie i odczytywanie operacji. Aby uzyskać więcej informacji, zobacz [przechowywanie i ładowanie obiektów CObjects za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md) w artykule serializacja: serializacja obiektu.  
  
> [!NOTE]
>  Nie należy mylić `CArchive` klasa o klasach iostream ogólnego przeznaczenia, które są do sformatowanego tekstu tylko. `CArchive` Klasy jest przeznaczony dla obiektów serializowanych formatu binarnego.  
  
 Jeśli chcesz, można pominąć serializacji MFC do tworzenia własnych mechanizm dla magazynu danych. Należy przesłonić funkcji elementów członkowskich klasy, które inicjują serializacji na polecenie użytkownika. Zawiera omówienie w [22 Uwaga techniczna](../mfc/tn022-standard-commands-implementation.md) z `ID_FILE_OPEN`, **id_file_save —**, i **id_file_save_as —** standardowych poleceń.  
  
 Następujące artykuły obejmuje dwa główne zadania wymagane do serializacji:  
  
-   [Serializacja: ustawianie klasy jako możliwej do serializacji](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)  
  
 Artykuł [szeregowanie: vs serializacji. Baza danych wejścia/wyjścia](../mfc/serialization-serialization-vs-database-input-output.md) opisuje po serializacji jest właściwa metoda wejścia/wyjścia w aplikacjach baz danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [CArchive — klasa](../mfc/reference/carchive-class.md)   
 [CObject — klasa](../mfc/reference/cobject-class.md)   
 [Cdocument — klasa](../mfc/reference/cdocument-class.md)   
 [Klasa CFile](../mfc/reference/cfile-class.md)
