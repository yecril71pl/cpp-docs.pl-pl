---
title: "Makra komunikatów systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::WM_FORWARDMSG
dev_langs: C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dde3255997b03eb827ef9e318de73b3badee23c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-messages-macros"></a>Makra komunikatów systemu Windows
To makro przekazuje komunikaty okna.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Służy do przesyłania dalej wiadomości przekazanej okno, aby inne okno dla przetwarzania.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 To makro przekazuje komunikat odebrany przez okno do innego okna do przetwarzania.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat został przetworzony, zero, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `WM_FORWARDMSG` do przekazywania komunikatów otrzymanych przez okno do innego okna do przetwarzania. Parametry LPARAM i WPARAM są używane w następujący sposób:  
  
|Parametr|Użycie|  
|---------------|-----------|  
|WPARAM|Dane zdefiniowane przez użytkownika|  
|LPARAM|Wskaźnik do `MSG` struktury, który zawiera informacje o wiadomości|  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie `m_hWndOther` reprezentuje okna odbierające ten komunikat.  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
