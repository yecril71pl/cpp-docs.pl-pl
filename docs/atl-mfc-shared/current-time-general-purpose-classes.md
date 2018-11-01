---
title: 'Bieżący czas: Klasy ogólnego przeznaczenia'
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
ms.openlocfilehash: e883a47243feb7ad1555748ffdda9b8ae9594644
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539259"
---
# <a name="current-time-general-purpose-classes"></a>Bieżący czas: Klasy ogólnego przeznaczenia

Poniższa procedura przedstawia sposób tworzenia `CTime` obiektu i zainicjować go w bieżącym czasem.

### <a name="to-get-the-current-time"></a>Aby uzyskać bieżący czas

1. Przydziel `CTime` obiektu w następujący sposób:

   [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]

   > [!NOTE]
   > Niezainicjowane `CTime` obiekty nie są inicjowane na prawidłową godzinę.

1. Wywołaj `CTime::GetCurrentTime` funkcję, aby uzyskać bieżącą godzinę od systemu operacyjnego. Ta funkcja zwraca `CTime` obiektu, który może służyć do ustawiania wartości `CTime`, wykonując następujące czynności:

   [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]

   Ponieważ `GetCurrentTime` jest statyczną funkcją składową z `CTime` klasy musi kwalifikować nazwy z nazwą klasy i operatora rozpoznawania zakresu (`::`), `CTime::GetCurrentTime()`.

Oczywiście dwa kroki opisane wcześniej mogą być połączone w pojedynczej instrukcji programu w następujący sposób:

[!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]
