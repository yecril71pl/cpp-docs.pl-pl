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
ms.openlocfilehash: 393138916bf29fd9adb5dceb0b8612b576b84e76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft Specific**  
  
 Przenosi ilość 128-bitowego, reprezentowane jako dwie liczb 64-bitowych `LowPart` i `HighPart`, z prawej strony według liczby bitów określonej `Shift` i zwraca niski 64-bitowy wyniku.  
  
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
 Niski 64 bity ilość 128-bitowe, które mają zostać przesunięte.  
  
 [in] `HighPart`  
 Wysoka 64 bity ilość 128-bitowe, które mają zostać przesunięte.  
  
 [in] `Shift`  
 Liczba bitów, które mają zostać przesunięte.  
  
## <a name="return-value"></a>Wartość zwracana  
 Niski 64 bity wyniku.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `Shift` Wartość jest zawsze modulo 64 tak, na przykład, jeśli wywołujesz `__shiftright128(0, 1, 64)`, funkcja zostanie przesunięte wysokiej części `0` bitów prawym przyciskiem myszy i zwraca część niski `0` i nie `1` , ponieważ w przeciwnym razie można się spodziewać.  
  
## <a name="example"></a>Przykład  
 Na przykład zobacz [__shiftleft128](../intrinsics/shiftleft128.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)