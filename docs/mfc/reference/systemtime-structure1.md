---
title: SYSTEMTIME Structure1 | Dokumentacja firmy Microsoft
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
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a0042adaa223fc5898c057f191f7b750fa230f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

