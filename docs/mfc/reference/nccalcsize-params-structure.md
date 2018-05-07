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
ms.openlocfilehash: 07db612cb6dbde0dd762cf709ac6040bbd836c4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS — Struktura
`NCCALCSIZE_PARAMS` Struktury informacjami, używanego przez aplikację podczas przetwarzania `WM_NCCALCSIZE` komunikat do obliczenia rozmiaru, pozycji i Nieprawidłowa zawartość obszaru klienckiego okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parametry  
 *rgrc*  
 Określa tablicę prostokąty. Pierwszy zawiera współrzędne nowego okna, który został przeniesiony lub zmiany rozmiaru. Drugi zawiera współrzędne okna przed został przeniesiony lub zmiany rozmiaru. Trzeci zawiera współrzędne obszaru klienckiego okna przed został przeniesiony lub zmiany rozmiaru. Jeśli okno jest oknem podrzędnym, współrzędne są względem obszaru klienckiego okna nadrzędnego. Jeśli okno jest oknem najwyższego poziomu, współrzędne są podawane względem ekranu.  
  
 *lppos*  
 Wskazuje [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) strukturę, która zawiera wartości rozmiar i położenie określony w operacji, który spowodował do przeniesienia lub zmiany rozmiaru okna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

