---
title: Nccalcsize_params — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 095b66af9dab08e3d8fad040c43e2eaf8d2beb81
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335646"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS — Struktura
`NCCALCSIZE_PARAMS` Struktura zawiera informacje, że aplikacja może użyć podczas przetwarzania komunikatu WM_NCCALCSIZE do obliczania rozmiarem, pozycją i prawidłową zawartość obszaru klienckiego okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parametry  
 *rgrc*  
 Określa tablicę prostokąty. Pierwszy zawiera współrzędne nowe okno które zostały przeniesione lub zmiany rozmiaru. Drugi zawiera współrzędne okna, zanim został on przeniesiony lub ze zmienionym rozmiarem. Trzeci zawiera współrzędne obszaru klienckiego okna, zanim został on przeniesiony lub ze zmienionym rozmiarem. Jeśli okno jest oknem podrzędnym, współrzędne są podawane względem pola klienta okna nadrzędnego. Jeśli okno jest oknem najwyższego poziomu, współrzędne są podawane względem ekranu.  
  
 *lppos*  
 Wskazuje [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) strukturę, która zawiera wartości rozmiaru i położenia określone w operacji, która spowodowała okna do przeniesienia lub zmiany rozmiaru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

