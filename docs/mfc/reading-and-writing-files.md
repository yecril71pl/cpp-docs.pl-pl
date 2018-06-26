---
title: Odczyt i zapis plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30ee5b326833b45365c422238ecfcd4f82c556d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930914"
---
# <a name="reading-and-writing-files"></a>Odczytywanie i zapisywanie danych pliku
Jeśli używano funkcje obsługi plików biblioteki wykonawczej języka C, będą wyświetlane znanych MFC operacji odczytu i zapisu. W tym artykule opisano odczytywanie bezpośrednio z oraz zapisywanie bezpośrednio do `CFile` obiektu. Użytkownik może również buforowane We/Wy plików z [CArchive](../mfc/reference/carchive-class.md) klasy.  
  
#### <a name="to-read-from-and-write-to-the-file"></a>Można odczytywać i zapisywać do pliku  
  
1.  Użyj `Read` i `Write` funkcji elementów członkowskich do odczytywania i zapisywania danych w pliku.  
  
     —lub—  
  
2.  `Seek` Funkcja członkowska jest również dostępny do przechodzenia do określonych przesunięcie w pliku.  
  
 `Read` pobiera wskaźnik buforu i liczby bajtów do odczytania i zwraca rzeczywistą liczbę bajtów, które zostały odczytane. Jeśli wymagana liczba bajtów nie można odczytać ponieważ końca pliku (EOF) zostanie osiągnięty, zwracany jest rzeczywista liczba bajtów odczytanych. W przypadku błędu odczytu jest zwracany wyjątek. `Write` przypomina `Read`, ale liczba zapisanych bajtów nie są zwracane. Jeśli wystąpi błąd, w tym bez zapisywania wszystkich bajtów jest określony, jest zwracany wyjątek. Jeśli masz prawidłową `CFile` obiektu można odczytać z niego lub w nim zapisywać, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  Zwykle należy przeprowadzić operacji wejścia/wyjścia w obrębie **spróbuj**/**catch** bloku obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków (MFC)](../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

