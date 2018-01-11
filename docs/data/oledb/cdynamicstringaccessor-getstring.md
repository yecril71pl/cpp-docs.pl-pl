---
title: CDynamicStringAccessor::GetString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs: C++
helpviewer_keywords: GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9fee0b531fa96d9767b28751e2dd8b3766278983
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
Pobiera dane określonej kolumny jako ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      BaseType* GetString(  
   DBORDINAL nColumn  
) const throw( );  
BaseType* GetString(  
   const CHAR* pColumnName  
) const throw( );  
BaseType* GetString(  
   const WCHAR* pColumnName  
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
 `pColumnName`  
 [in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wartości ciągu jest pobierana z określonej kolumny. Wartość jest typu ***BaseType***, który będzie **CHAR** lub **WCHAR** w zależności od tego, czy jest zdefiniowana _unicode —, czy nie. Zwraca wartość NULL, jeśli nie można odnaleźć określonej kolumny.  
  
## <a name="remarks"></a>Uwagi  
 Drugi zastąpić formularza przyjmuje nazwy kolumny jako ciągu ANSI. Trzeci zastąpić formularza przyjmuje nazwy kolumny jako ciąg Unicode.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)