---
title: Struktura PAINTSTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92583bba3dca60caa2895966a87571dc60805475
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="paintstruct-structure"></a>Struktura PAINTSTRUCT
`PAINTSTRUCT` Struktura zawiera informacje, który może służyć do malowania obszaru klienckiego okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *elementu hdc*  
 Identyfikuje kontekst wyświetlania służący do rysowania.  
  
 *fErase*  
 Określa, czy tło powinien być narysowany ponownie. Nie jest równa 0, jeśli aplikacja powinna ponownie narysuj tła. Aplikacja jest odpowiedzialny za rysowania tła. Jeśli klasę okna systemu Windows została utworzona bez pędzel tła (zobacz opis **hbrBackground** członkiem [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) — struktura w systemie Windows SDK).  
  
 *rcPaint*  
 Określa lewy górny i dolny prawy narożników prostokąta, w którym wymagane jest rysowania.  
  
 *fRestore*  
 Zastrzeżonym elementem członkowskim. Jest ona używana wewnętrznie przez system Windows.  
  
 *fIncUpdate*  
 Zastrzeżonym elementem członkowskim. Jest ona używana wewnętrznie przez system Windows.  
  
 *rgbReserved [16]*  
 Zastrzeżonym elementem członkowskim. Zarezerwowane blok pamięci używana wewnętrznie przez system Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

