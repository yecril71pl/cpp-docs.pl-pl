---
title: "Odczyt i zapis plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 770dfe28b3f0278ba2682b37b71d1dd89d02ae2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reading-and-writing-files"></a>Odczytywanie i zapisywanie danych pliku
Jeśli używano funkcje obsługi plików biblioteki wykonawczej języka C, będą wyświetlane znanych MFC operacji odczytu i zapisu. W tym artykule opisano odczytywanie bezpośrednio z oraz zapisywanie bezpośrednio do `CFile` obiektu. Użytkownik może również buforowane We/Wy plików z [CArchive](../mfc/reference/carchive-class.md) klasy.  
  
#### <a name="to-read-from-and-write-to-the-file"></a>Można odczytywać i zapisywać do pliku  
  
1.  Użyj **odczytu** i **zapisu** funkcji elementów członkowskich do odczytywania i zapisywania danych w pliku.  
  
     —lub—  
  
2.  `Seek` Funkcja członkowska jest również dostępny do przechodzenia do określonych przesunięcie w pliku.  
  
 **Odczyt** przyjmuje wskaźnika buforu i liczby bajtów do odczytania i zwraca rzeczywistą liczbę bajtów, które zostały odczytane. Jeśli wymagana liczba bajtów nie można odczytać ponieważ końca pliku (EOF) zostanie osiągnięty, zwracany jest rzeczywista liczba bajtów odczytanych. W przypadku błędu odczytu jest zwracany wyjątek. **Zapis** jest podobny do **odczytu**, ale liczba zapisanych bajtów nie są zwracane. Jeśli wystąpi błąd, w tym bez zapisywania wszystkich bajtów jest określony, jest zwracany wyjątek. Jeśli masz prawidłową `CFile` obiektu można odczytać z niego lub w nim zapisywać, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  Zwykle należy przeprowadzić operacji wejścia/wyjścia w obrębie **spróbuj**/**catch** bloku obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków (MFC)](../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

