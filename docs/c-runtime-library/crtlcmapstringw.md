---
title: __crtLCMapStringW | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __crtLCMapStringW
dev_langs:
- C++
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b12bdb89a038ccd420748c1b855f21e1b9e4d93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW
Mapuje jedną ciągu znaków do drugiego wykonywania określone przekształcenie zależnych od ustawień regionalnych. Tej funkcji można również generowanie klucza sortowania dla ciągu wejściowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int __crtLCMapStringW(  
   LCID    Locale,  
   DWORD   dwMapFlags,  
   LPCWSTR lpSrcStr,  
   int     cchSrc,  
   LPWSTR  lpDestStr,  
   int     cchDest)  
```  
  
#### <a name="parameters"></a>Parametry  
 `Locale`  
 Identyfikator ustawień regionalnych. Ustawienia regionalne dostarcza kontekst dla mapowania ciągu lub generowania kluczy sortowania. Aplikacja może użyć `MAKELCID` makra w celu utworzenia identyfikator ustawień regionalnych.  
  
 `dwMapFlags`  
 Typ transformacji mają być użyte podczas ciąg mapowania lub sortowania generowania kluczy.  
  
 `lpSrcStr`  
 Wskaźnik do funkcji mapuje lub korzysta z sortowania generowania kluczy ciąg źródła. Ten parametr zakłada się, że ciąg Unicode.  
  
 `cchSrc`  
 Rozmiar w znaków ciągu wskazywana przez `lpSrcStr` parametru. Ten licznik można uwzględnić terminatorem NULL lub nie ma.  
  
 A `cchSrc` wartość -1 określa ciąg wskazywana przez `lpSrcStr` jest zerem. Jeśli jest to możliwe, a ta funkcja jest używany w trybie mapowania ciągów, funkcja obliczy długość ciągu, sama i null kończy zamapowanych ciąg przechowywane w `*lpDestStr`.  
  
 `lpDestStr`  
 Długie wskaźnik do buforu, w której funkcja przechowuje zamapowanych klucz ciągu lub sortowania.  
  
 `cchDest`  
 Rozmiar w znakach bufor wskazywany przez `lpDestStr`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość `cchDest` jest różna od zera, liczba znaków lub bajtów Jeśli `LCMAP_SORTKEY` jest określony, zapisywane w buforze oznacza Powodzenie. Licznik ten uwzględnia również miejsce dla terminatora o wartości NULL.  
  
 Jeśli wartość `cchDest` jest 0, rozmiar buforu znaków lub liczbę bajtów Jeśli `LCMAP_SORTKEY` określono wymagane do odbierania przetłumaczonego ciągu lub sortowania klucza oznacza Powodzenie. Ten rozmiar miejscem terminatorem NULL.  
  
 Zero oznacza błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError` funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `cchSrc` jest większa od zera i `lpSrcStr` jest ciągiem zakończonym znakiem null `__crtLCMapStringW` ustawia `cchSrc` do długości ciągu. Następnie `__crtLCMapStringW` wywołuje wersji szeroki ciąg (Unicode) `LCMapString` funkcji z określonymi parametrami. Aby uzyskać więcej informacji o tych parametrów i wartości zwracanej przez tę funkcję, zobacz `LCMapString` działać przy [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__crtLCMapStringW|awint.h|