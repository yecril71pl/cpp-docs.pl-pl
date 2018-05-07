---
title: MSG Structure1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dbbcdd3404705a9ac7c6c7969a9ebeeb0238f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

