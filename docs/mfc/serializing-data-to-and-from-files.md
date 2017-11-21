---
title: "Serializacja danych do i z plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a0b81c90567bb3cebd9a5e128eb6b76d58ee9b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="serializing-data-to-and-from-files"></a>Serializacja danych do plików i z plików
Zgodnie z podstawową koncepcją trwałości jest, że obiekt powinien mieć możliwość zapisywania swojego bieżącego stanu wskazanych przez wartości jego zmienne Członkowskie do magazynu trwałego. Później obiekt można ponownie utworzyć za odczytywanie lub "deserializacji", stan obiektu z magazynu trwałego. W tym miejscu klucza punktu jest odpowiedzialny za odczytywanie i zapisywanie własny stan samego obiektu. W związku z tym dla klasy były trwałe, musi on implementować operacji podstawowe serializacji.  
  
 Platformę udostępnia domyślną implementację dla zapisywanie do plików dysku w odpowiedzi na zapisywanie dokumentów i Zapisz jako polecenia w menu Plik i ładowania z dysku w odpowiedzi na polecenie Otwórz dokumenty. Z bardzo małego wysiłku można zaimplementować dokumentu możliwość zapisu i odczytu danych do i z pliku. Główne operacją, należy wykonać, jest zastąpienie [serializacja](../mfc/reference/cobject-class.md#serialize) funkcji członkowskiej we własnej klasy dokumentu.  
  
 Kreator aplikacji MFC umieszcza szkieletowych zastępowania **CDocument** funkcji członkowskiej `Serialize` w klasie dokumentów, tworzy dla Ciebie. Po wdrożeniu aplikacji zmienne Członkowskie, można wypełnić Twojej `Serialize` zastąpienia z kodem, który wysyła dane do "archiwum do obiektu" podłączone do pliku. A [CArchive](../mfc/reference/carchive-class.md) obiektu jest podobny do `cin` i `cout` wejścia/wyjścia obiektów z biblioteki iostream C++. Jednak `CArchive` zapisuje i odczytuje formatu binarnego, nie jest sformatowany tekst.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Serializacja](../mfc/serialization-in-mfc.md)  
  
-   [Rola dokumentu w serializacji](#_core_the_document.92.s_role_in_serialization)  
  
-   [Rola danych w serializacji](#_core_the_data.92.s_role_in_serialization)  
  
-   [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a>Rola dokumentu w serializacji  
 Platformę automatycznie odpowiada Otwórz menu Plik, Zapisz i Zapisz jako polecenia przez wywołanie dokumentu `Serialize` funkcji członkowskiej, jeśli jest stosowana. `ID_FILE_OPEN` Polecenia, na przykład wywołuje funkcję obsługi wewnątrz obiektu application. W trakcie tego procesu użytkownik widzi i odpowiada okno dialogowe Otwieranie pliku i ramach uzyskuje nazwę pliku, który użytkownik wybierze. Tworzy w ramach `CArchive` obiektu ustawione dla ładowania danych do dokumentu i przekazuje archiwum do `Serialize`. Plik został już otwarty przez platformę. Kod w Twoim dokumencie `Serialize` funkcji członkowskiej odczytuje dane w za pomocą archiwum Rekonstruowanie obiekty danych, zgodnie z potrzebami. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [szeregowanie](../mfc/serialization-in-mfc.md).  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a>Rola danych w serializacji  
 Ogólnie rzecz biorąc typu klasy danych powinno być możliwe do serializacji sam. Oznacza to gdy obiekt przekazywany do archiwum, obiekt wiedzieć, sposób sam zapisać w archiwum i samego odczytywać archiwum. MFC zapewnia obsługę dokonywania klas serializacji w ten sposób. W przypadku projektowania klasę, aby zdefiniować typu danych i planuje serializować dane tego typu projektu dla serializacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)

