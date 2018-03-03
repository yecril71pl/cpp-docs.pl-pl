---
title: "_setjmp3 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72bc1e833ddaa72979e25274b7328d8987f62763
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setjmp3"></a>_setjmp3
Funkcji CRT wewnętrznej. Nowe implementacja `setjmp` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _setjmp3(  
   OUT jmp_buf env,  
   int count,  
   (optional parameters)  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`env`  
 Adres buforu do przechowywania informacji o stanie.  
  
 [in]`count`  
 Liczba dodatkowych `DWORD`s informacje, które są przechowywane w `optional parameters`.  
  
 [in]`optional parameters`  
 Dodatkowe dane przesuwana przez `setjmp` wewnętrznej. Pierwszy `DWORD` jest wskaźnik funkcji, służący do dodatkowe dane operacji unwind i wrócić do nieulotnej zarejestrować stanu. Drugi `DWORD` poziom spróbuj przywrócić. Wszystkie dalsze dane są zapisywane w tablicy danych typu ogólnego w `jmp_buf`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 Nie należy używać tej funkcji w programie C++. Jest wewnętrzna funkcja, która nie obsługuje języka C++. Aby uzyskać więcej informacji o sposobie używania `setjmp`, zobacz [użycie funkcji setjmp/longjmp](../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)