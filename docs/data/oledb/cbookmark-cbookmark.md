---
title: CBookmark::CBookmark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a996f397da3516a43a3e56840d159a070269ff8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
Konstruktor.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      CBookmark();   

CBookmark(DBLENGTH nSize);  
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