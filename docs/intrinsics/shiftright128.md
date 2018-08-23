---
title: __shiftright128 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0aa5b4028863ff31084e8d01892a86b990de51fb
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465979"
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft Specific**  
  
 Przenosi ilość 128-bitowego, reprezentowane jako dwie ilości 64-bitowych `LowPart` i `HighPart`, w prawo o liczbę bitów określoną przez `Shift` i zwraca niski 64 bity wyniku.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `LowPart`  
 Niski 64 bity ilość 128-bitowe przesunięcie.  
  
 [in] `HighPart`  
 Wysoka 64 bity ilość 128-bitowe przesunięcie.  
  
 [in] `Shift`  
 Liczba bitów, aby przesunąć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Niski 64 bity wyniku.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__shiftright128`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `Shift` Wartość jest zawsze modulo 64 więc, na przykład, jeśli wywołasz `__shiftright128(0, 1, 64)`, funkcja zostanie wprowadzony wysokiej część `0` bitów, kliknij prawym przyciskiem myszy i powrócić niskiej część `0` i nie `1` w przeciwnym razie może być oczekiwany.  
  
## <a name="example"></a>Przykład  
 Aby uzyskać przykład, zobacz [__shiftleft128](../intrinsics/shiftleft128.md).  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)