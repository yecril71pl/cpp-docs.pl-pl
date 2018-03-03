---
title: "Bieżący czas: Ogólnego przeznaczenia klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6c43ffd60d837bdd8f061057cf1c36340b6e6af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="current-time-general-purpose-classes"></a>Bieżący czas: Klasy ogólnego przeznaczenia
Poniższa procedura przedstawia sposób tworzenia `CTime` i zainicjować go przy użyciu bieżącego czasu.  
  
#### <a name="to-get-the-current-time"></a>Aby uzyskać bieżącą godzinę  
  
1.  Przydziel `CTime` obiektu, w następujący sposób:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  Niezainicjowany `CTime` obiekty nie są inicjowane na czas ważności.  
  
2.  Wywołanie `CTime::GetCurrentTime` funkcji, aby uzyskać bieżącą godzinę z systemu operacyjnego. Ta funkcja zwraca `CTime` obiekt, który może służyć do ustawienia wartości `CTime`w następujący sposób:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]  
  
     Ponieważ `GetCurrentTime` jest statycznej funkcji członkowskiej z `CTime` klasy, muszą kwalifikować się jego nazwę, wraz z nazwą klasy i operator rozpoznawania zakresów (`::`), `CTime::GetCurrentTime()`.  
  
 Oczywiście dwa kroki opisane wcześniej można łączyć w jednej instrukcji programu w następujący sposób:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina: klasy ogólnego przeznaczenia](../atl-mfc-shared/date-and-time-general-purpose-classes.md)



