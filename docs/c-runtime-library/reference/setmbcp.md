---
title: "_setmbcp — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
dev_langs: C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b09953ffdb1523078f31cad08d53253b9d79892
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setmbcp"></a>_setmbcp
Ustawia nowej strony kodowe wielobajtowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codepage`  
 Nowe ustawienie strony kodowej dla procedury wielobajtowe niezależne od ustawień regionalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli pomyślnie ustawiono na stronę kodową. Jeśli podano nieprawidłowy strony kodowej dla `codepage`, zwraca -1 i ustawienie strony kodowej jest bez zmian. Ustawia `errno` do `EINVAL` Jeśli wystąpi błąd alokacji pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `_setmbcp` Funkcja określa nowej strony kodowe wielobajtowe. Domyślnie system środowiska wykonawczego automatycznie ustawia strony kodowe wielobajtowe systemu domyślną stronę kodową ANSI. Ustawienia strony kodowe wielobajtowe ma wpływ na wszystkie wielobajtowe procedury, które nie są zależne ustawień regionalnych. Jednak użytkownik może nakazać programowi `_setmbcp` do użycia na stronę kodową zdefiniowane dla bieżącego ustawienia regionalne (zobacz poniższą listę stałych manifestu i skojarzone zachowanie wyników). Lista wielobajtowe procedur, które są zależne od strona kodowa ustawień lokalnych, a nie strony kodowe wielobajtowe, zobacz [interpretacji znaków wielobajtowych sekwencji](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).  
  
 Strony kodowe wielobajtowe dotyczy również przetwarzanie znaków wielobajtowych przy użyciu poniższych procedur biblioteki wykonawczej:  
  
||||  
|-|-|-|  
|[_exec — funkcje](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp —](../../c-runtime-library/reference/mktemp-wmktemp.md)|[_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[_fullpath —](../../c-runtime-library/reference/fullpath-wfullpath.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam —](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[_makepath —](../../c-runtime-library/reference/makepath-wmakepath.md)|[_splitpath —](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam —](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 Ponadto wszystkie procedury biblioteki wykonawczej otrzymujących znaków wielobajtowych `argv` lub `envp` program argumenty jako parametry (takie jak `_exec` i `_spawn` rodzin) przetworzyć te ciągi zgodnie ze strony kodowe wielobajtowe . W związku z tym te procedury dotyczy także przez wywołanie do `_setmbcp` zmienia się strony kodowe wielobajtowe.  
  
 `codepage` Argument może być ustawiony na jedną z następujących wartości:  
  
-   `_MB_CP_ANSI`Użyj strony kodowej ANSI uzyskane z systemu operacyjnego podczas uruchamiania programu.  
  
-   `_MB_CP_LOCALE`Użyj strony kodowej bieżące ustawienia regionalne uzyskane z poprzedniego wywołania [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   `_MB_CP_OEM`Strona kodowa używana przez producenta OEM uzyskane z systemu operacyjnego podczas uruchamiania programu.  
  
-   `_MB_CP_SBCS`Użyj strony kodowej jednobajtowe. Jeśli strona kodowa jest równa `_MB_CP_SBCS`, procedur, takich jak [_ismbblead —](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) zawsze zwraca wartość false.  
  
-   Wszelkie inne prawidłowy kod strony wartości, niezależnie od tego, czy wartość jest ANSI, OEM lub inne strony kodu działania systemu — obsługiwane (z wyjątkiem UTF-7 i UTF-8, które nie są obsługiwane).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_setmbcp`|\<mbctype.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [_getmbcp —](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)