---
title: CBookmark::CBookmark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs: C++
helpviewer_keywords: CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 63d5bef87a50b5027a743e9927f22c84636c1c9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
Konstruktor.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      CBookmark( );   
CBookmark(  
   DBLENGTH nSize   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nSize`  
 [in] Rozmiar buforu zakładki w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Pierwsza funkcja ustawia bufor **NULL** i rozmiar buforu na 0. Druga funkcja ustawia rozmiar buforu `nSize`, a bufor tablicy bajtów `nSize` bajtów.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w **CBookmark\<0 >**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CBookmark, klasa](../../data/oledb/cbookmark-class.md)