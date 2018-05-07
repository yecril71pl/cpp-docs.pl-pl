---
title: CBookmark::CBookmark | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7663c34fc9eea5f4262fea6b347c1b7899ace85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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