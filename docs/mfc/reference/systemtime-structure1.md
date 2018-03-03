---
title: SYSTEMTIME Structure1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07af222a3d51ff1cc71076d5bbcc3513a3d6cad4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="systemtime-structure1"></a>SYSTEMTIME Structure1
`SYSTEMTIME` Struktury reprezentuje datę i godzinę za pomocą poszczególnych członków dla miesiąc, dzień, roku, dzień tygodnia, godziny, minuty, sekundy i milisekund.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _SYSTEMTIME {  
    WORD wYear;  
    WORD wMonth;  
    WORD wDayOfWeek;  
    WORD wDay;  
    WORD wHour;  
    WORD wMinute;  
    WORD wSecond;  
    WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### <a name="parameters"></a>Parametry  
 *wYear*  
 Bieżącego roku.  
  
 *wartość zero*  
 W bieżącym miesiącu; Stycznia wynosi 1.  
  
 *Może*  
 Bieżący dzień tygodnia; Niedziela wynosi 0, od poniedziałku 1 i tak dalej.  
  
 *Członka*  
 Bieżący dzień miesiąca.  
  
 *wDayOfWeek*  
 Bieżąca godzina.  
  
 *Dnia*  
 Bieżącej minuty.  
  
 *Poprzez*  
 Bieżącej sekundy.  
  
 *wMilliseconds*  
 Bieżący milisekund.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

