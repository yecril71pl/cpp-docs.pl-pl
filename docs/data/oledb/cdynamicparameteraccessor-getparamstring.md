---
title: CDynamicParameterAccessor::GetParamString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
dev_langs:
- C++
helpviewer_keywords:
- GetParamString method
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8dadcb70dd29f1a70aea288eb0f63b22591561e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamstring"></a>CDynamicParameterAccessor::GetParamString
Pobiera dane ciągu określonego parametru przechowywane w buforze.  
  
## <a name="syntax"></a>Składnia  
  
```
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowana dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego kolejności w języku SQL lub procedurę składowaną wywołania. Zobacz [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 `strOutput`  
 [out] ANSI (**CSimpleStringA**) lub Unicode (**CSimpleStringW**) dane określony parametr ciągu. Należy przekazać parametr typu `CString`, na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 [out] Wskaźnik do ANSI (**CHAR**) lub Unicode (**WCHAR**) dane określony parametr ciągu.  
  
 `pMaxLen`  
 [out] Wskaźnik do rozmiaru buforu wskazywana przez `pBuffer` (w znakach, tym zakończenia NULL).  
  
## <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
 Jeśli `pBuffer` ma wartość NULL, ta metoda ustawi wymagany rozmiar buforu w pamięci, do których prowadzą `pMaxLen` i zwracać **true** bez kopiowania danych.  
  
 Ta metoda zakończy się niepowodzeniem, jeśli bufor `pBuffer` nie jest wystarczająco duży, aby zawierać całe ciągi.  
  
 Użyj `GetParamString` można pobrać dane parametru ciągu z buforu. Użyj [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) można pobrać danych parametru typu z buforu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)