---
title: 'Data i godzina: Obsługa SYSTEMTIME | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf48881b3baeb7dc5ab48483ae9b075a9c048a38
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883570"
---
# <a name="date-and-time-systemtime-support"></a>Data i godzina: Obsługa SYSTEMTIME
[CTime](../atl-mfc-shared/reference/ctime-class.md) klasa ma konstruktory, które akceptują czasu systemu i plików z systemu Win32. Jeśli używasz `CTime` obiektów w tym celu należy zmodyfikować inicjalizacji w związku z tym zgodnie z opisem w tym artykule.  
  
 Aby uzyskać informacje o struktura SYSTEMTIME, zobacz [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Aby uzyskać informacje o struktura FILETIME, zobacz [FILETIME](../mfc/reference/filetime-structure.md).  
  
 Biblioteka MFC nadal zawiera `CTime` konstruktorów, które przyjmują argumentów czasu w stylu systemu MS-DOS, ale, począwszy od wersji 3.0, MFC `CTime` klasy obsługuje również konstruktora przyjmującego Win32 `SYSTEMTIME` struktury i drugiego, która przyjmuje Win32 `FILETIME` struktury.  
  
 Nowy `CTime` konstruktory są:  
  
-   CTime (const SYSTEMTIME & `sysTime`);  
  
-   CTime (const FILETIME & `fileTime`);  
  
 *FileTime* parametr to odwołanie do systemu Win32 `FILETIME` strukturę, która reprezentuje godzinę jako wartość 64-bitowych, bardziej wygodne formatu dla magazynu wewnętrznego niż `SYSTEMTIME` struktury i format używany przez systemu Win32 w celu reprezentuje czas tworzenia pliku.  
  
 Jeśli kod zawiera `CTime` obiekt został zainicjowany z czasem systemowym, należy użyć `SYSTEMTIME` konstruktora w systemie Win32.  
  
 Najprawdopodobniej nie będzie używać `CTime` `FILETIME` inicjowania bezpośrednio. Jeśli używasz `CFile` obiekt do manipulowania plikiem [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) pobiera sygnatura czasowa pliku dla za pomocą `CTime` obiekt inicjowany za pomocą `FILETIME` struktury.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat  
  
-   [Ogólne Data i godzina programowania w MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Obsługa automatyzacji daty i godziny programowania](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Klasy ogólnego przeznaczenia dla daty i godziny programowania](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina](../atl-mfc-shared/date-and-time.md)

