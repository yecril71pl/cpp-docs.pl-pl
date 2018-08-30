---
title: Struktura PAINTSTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dddf9c117f2366496609f8bdf4ffc2f069f66ace
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199576"
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
 Identyfikuje kontekst wyświetlania ma być używany do malowania.  
  
 *fErase*  
 Określa, czy tło powinien być narysowany ponownie. Nie jest równa 0, jeśli aplikacja ponownie narysować tła. Aplikacja jest odpowiedzialna za rysowania tła, jeśli klasę okna Windows została utworzona bez pędzel tła (zobacz opis `hbrBackground` członkiem [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury w zestawie Windows SDK).  
  
 *rcPaint*  
 Określa lewym górnym i dolnym prawym rogu prostokąta, w której zażądano malowania.  
  
 *fRestore*  
 Zastrzeżoną składową. Jest ono używane wewnętrznie przez Windows.  
  
 *fIncUpdate*  
 Zastrzeżoną składową. Jest ono używane wewnętrznie przez Windows.  
  
 *rgbReserved [16]*  
 Zastrzeżoną składową. Zastrzeżone blok pamięć używana wewnętrznie przez Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

