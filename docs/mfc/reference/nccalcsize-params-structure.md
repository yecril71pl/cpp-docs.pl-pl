---
title: "Nccalcsize_params — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76a0a16ff0a2c90c6dd6060badc2c79dde1af231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

