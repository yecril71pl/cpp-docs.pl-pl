---
title: CDynamicStringAccessor::SetString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs: C++
helpviewer_keywords: SetString method
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c05186d8ea7f62ad07cae9a4b4689083543e485
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicstringaccessorsetstring"></a>CDynamicStringAccessor::SetString
Ustawia dane określonej kolumny jako ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Specjalna wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
 `pColumnName`  
 [in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.  
  
 `data`  
 [in] Wskaźnik do danych ciągu do zapisania do określonej kolumny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wartości ciągu, do którego można ustawić określonej kolumny. Wartość jest typu `BaseType`, który będzie `CHAR` lub `WCHAR` w zależności od tego, czy `_UNICODE` lub nie jest zdefiniowana.  
  
## <a name="remarks"></a>Uwagi  
 Drugi zastąpienia formularza przyjmuje nazwę kolumny w postaci ciągu ANSI i trzeci Zastąp formularz przyjmuje nazwy kolumny jako ciąg Unicode.  
  
 Jeśli `_SECURE_ATL` zdefiniowano będzie mieć wartość niezerową, zostaną wygenerowane Błąd potwierdzenia środowiska uruchomieniowego, jeśli dane wejściowe `data` string jest dłuższy niż maksymalną dozwoloną długość kolumny danych występujące w odwołaniu. W przeciwnym razie ciąg wejściowy zostanie obcięty w przypadku przekracza maksymalną dozwoloną długość.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)