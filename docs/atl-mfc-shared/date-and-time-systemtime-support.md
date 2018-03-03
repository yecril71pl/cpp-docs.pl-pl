---
title: "Data i godzina: Obsługa SYSTEMTIME | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 405c245cdab6426330915c945cd77f8336e68c9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="date-and-time-systemtime-support"></a>Data i godzina: Obsługa SYSTEMTIME
[Ctime —](../atl-mfc-shared/reference/ctime-class.md) klasa ma konstruktorów akceptujących czas systemu i plik z Win32. Jeśli używasz `CTime` obiektów w tym celu należy zmodyfikować inicjalizacji odpowiednio, zgodnie z opisem w tym artykule.  
  
 Aby uzyskać informacje o struktura SYSTEMTIME, zobacz [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Aby uzyskać informacje o struktura FILETIME, zobacz [FILETIME](../mfc/reference/filetime-structure.md).  
  
 MFC nadal zawiera `CTime` konstruktorów przyjmujących argumentów czasu w stylu MS-DOS, ale, począwszy od wersji 3.0 lub nowszej, MFC `CTime` klasa obsługuje również konstruktora przyjmującego Win32 `SYSTEMTIME` struktury oraz inne, które przyjmuje Win32 `FILETIME` struktury.  
  
 Nowe `CTime` konstruktory są:  
  
-   Ctime — (const SYSTEMTIME & `sysTime`);  
  
-   Ctime — (const FILETIME & `fileTime`);  
  
 `fileTime` Parametr jest odwołanie do Win32 `FILETIME` struktury, która reprezentuje czas jako wartość 64-bitowy format wygodniejsze dla magazynu wewnętrznego niż `SYSTEMTIME` struktury i format używany przez Win32 do reprezentowania czasu pliku Tworzenie.  
  
 Jeśli w kodzie `CTime` obiektu zainicjowany z czasem systemowym, należy użyć `SYSTEMTIME` konstruktora w Win32.  
  
 Prawdopodobnie nie będzie używać `CTime` `FILETIME` inicjowania bezpośrednio. Jeśli używasz `CFile` obiekt do manipulowania pliku [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) pobiera sygnatury czasowej pliku dla Ciebie za pośrednictwem `CTime` zainicjować obiektu z `FILETIME` struktury.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Ogólne Data i godzina Programowanie w MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Obsługa automatyzacji daty i czasu programowania](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Klasy ogólnego przeznaczenia dla daty i czasu programowania](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina](../atl-mfc-shared/date-and-time.md)

