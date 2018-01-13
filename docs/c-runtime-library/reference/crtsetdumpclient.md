---
title: "_Crtsetdumpclient — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetDumpClient
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs: C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf64ca280998ac25adbb380ff8245a0b8eecf797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient
Instaluje funkcji zdefiniowanych przez aplikację do zrzutu `_CLIENT_BLOCK` wpisz bloki pamięci (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dumpClient`  
 Nową funkcję zrzutu pamięci zdefiniowane przez klienta do przyłączanie się do procesu zrzutu pamięci środowiska wykonawczego debugowania C.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca bloku klienta wcześniej zdefiniowanego zrzutu funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtSetDumpClient` Funkcja umożliwia utworzenie punktu zaczepienia ma własną funkcję zrzutu obiektów przechowywanych w aplikacji `_CLIENT_BLOCK` bloki pamięci w czasie wykonywania C debugowania procesu zrzutu pamięci. W związku z tym, co razem, kiedy debugowania zrzutu funkcji takich jak [_crtmemdumpallobjectssince —](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) lub [_crtdumpmemoryleaks —](../../c-runtime-library/reference/crtdumpmemoryleaks.md) zrzuty `_CLIENT_BLOCK` blok pamięci aplikacji zrzutu funkcja jest wywoływana, jak również. `_CrtSetDumpClient`dostarcza aplikację łatwa metoda wykrywanie przecieków pamięci i sprawdzania poprawności lub reporting zawartości danych przechowywanych w `_CLIENT_BLOCK` bloków. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtSetDumpClient` są usuwane podczas przetwarzania wstępnego.  
  
 `_CrtSetDumpClient` Funkcja instaluje nowej funkcji zdefiniowanych przez aplikację zrzutu określone w `dumpClient` i zwraca funkcję wcześniej zdefiniowanego zrzutu. Przykładem funkcji zrzutu bloku klienta jest następujący:  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` Argument jest wskaźnik do początku części danych użytkownika blok pamięci i `blockSize` Określa rozmiar pamięci przydzielony blok w bajtów. Funkcja zrzutu bloku klienta musi zwracać `void`. Wskaźnik do funkcji zrzutu klienta, które są przekazywane do `_CrtSetDumpClient` jest typu `_CRT_DUMP_CLIENT`, zgodnie z definicją w Crtdbg.h:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 Aby uzyskać więcej informacji na temat funkcji, które pracują na `_CLIENT_BLOCK` wpisz bloki pamięci, zobacz [funkcji punktów zaczepienia bloku klienta](/visualstudio/debugger/client-block-hook-functions). [_Crtreportblocktype —](../../c-runtime-library/reference/crtreportblocktype.md) funkcja może służyć do zwracania informacji dotyczących typów bloku i podtypów.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_Crtreportblocktype —](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)