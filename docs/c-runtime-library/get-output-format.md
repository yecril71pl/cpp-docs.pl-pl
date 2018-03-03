---
title: "_get_output_format — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
dev_langs:
- C++
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30ee8de9c39d2b7e1fc6f9cf0a717120c95e92c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getoutputformat"></a>_get_output_format
Pobiera bieżącą wartość flagi format danych wyjściowych.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned int _get_output_format();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość flagi format danych wyjściowych.  
  
## <a name="remarks"></a>Uwagi  
 Flaga format danych wyjściowych Określa funkcje sformatowany operacji We/Wy. Obecnie flaga ma dwa możliwe wartości: 0 i `_TWO_DIGIT_EXPONENT`. Jeśli `_TWO_DIGIT_EXPONENT` ustawiono wartość zmiennoprzecinkowa drukowane numery punktu z dwie cyfry wykładnika, chyba że trzecia cyfra jest wymagany przez rozmiar wykładnik. Flaga wynosi zero, zmiennoprzecinkowych danych wyjściowych zawiera trzy cyfry wykładnik, przy użyciu wartości zerowe, jeśli to konieczne uzupełnić wartość do trzech cyfr.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_output_format`|\<stdio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
[Składnia specyfikacji formatu: funkcje printf i wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)  
 [printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf_s —, _printf_s_l —, wprintf_s — _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_set_output_format](../c-runtime-library/set-output-format.md)  
