---
title: MSG Structure1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b504f116dcbff7fa45e741ff9715070ee0c74583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="msg-structure1"></a>MSG Structure1
`MSG` Struktura zawiera informacje dotyczące komunikatu z kolejki komunikatów dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagMSG {     // msg    
    HWND hwnd;  
    UINT message;  
    WPARAM wParam;  
    LPARAM lParam;  
    DWORD time;  
    POINT pt;  
} MSG;  
```  
  
#### <a name="parameters"></a>Parametry  
 *Właściwość hwnd*  
 Określa okno, którego procedurę okna odbiera wiadomości.  
  
 `message`  
 Określa numer komunikatu.  
  
 `wParam`  
 Określa dodatkowe informacje na temat wiadomości. Dokładne znaczenie zależy od wartości **komunikat** elementu członkowskiego.  
  
 `lParam`  
 Określa dodatkowe informacje na temat wiadomości. Dokładne znaczenie zależy od wartości **komunikat** elementu członkowskiego.  
  
 `time`  
 Określa czas, w którym była umieszczona wiadomości.  
  
 `pt`  
 Określa pozycji kursora, we współrzędnych ekranu, gdy wiadomość była umieszczona.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

