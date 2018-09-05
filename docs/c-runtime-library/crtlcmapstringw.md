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
ms.openlocfilehash: 163d6f90d31e27cc4d8a616074f7f4153ab58876
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685498"
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW
Mapuje jeden ciąg znaków do innego, wykonując określone przekształcenie zależne od ustawień regionalnych. Tej funkcji można również wygenerować klucz sortowania dla ciągu wejściowego.  
  
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
 Identyfikator ustawień regionalnych. Ustawienia regionalne dostarcza kontekst dla mapowania ciągu lub generowania klucza sortowania. Aplikacja może użyć `MAKELCID` makra, aby utworzyć identyfikator ustawień regionalnych.  
  
 `dwMapFlags`  
 Typ przekształcenia, które będą używane w ciągu mapowania lub Sortuj generowania klucza.  
  
 `lpSrcStr`  
 Wskaźnik do ciągu źródłowym, funkcja mapuje lub używa do generowania klucza sortowania. Ten parametr będzie traktowana jako ciąg Unicode.  
  
 `cchSrc`  
 Rozmiar, w postaci ciągu, wskazywana przez `lpSrcStr` parametru. Ten licznik można uwzględnić terminator o wartości null lub nie ma.  
  
 A `cchSrc` wartość -1, określa ciąg wskazywany przez `lpSrcStr` jest zakończony znakiem null. Jeśli jest to możliwe, a ta funkcja jest używany w trybie mapowania ciągów, funkcja oblicza długość ciągu, sama i wartość null kończy ciąg zamapowany, przechowywane w `*lpDestStr`.  
  
 `lpDestStr`  
 Długie wskaźnik do buforu, w którym funkcja przechowuje zamapowanego klucza ciągu lub sortowania.  
  
 `cchDest`  
 Rozmiar w znakach bufor wskazywany przez `lpDestStr`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość `cchDest` jest różna od zera, liczba znaków, lub liczbę bajtów Jeśli `LCMAP_SORTKEY` jest określić, zapisywane w buforze oznacza sukces. Licznik ten uwzględnia również miejsce dla terminator o wartości null.  
  
 Jeśli wartość `cchDest` jest zero, rozmiaru buforu znaków lub liczbę bajtów Jeżeli `LCMAP_SORTKEY` jest określona, wymagane do odbierania przetłumaczonego ciągu lub Sortuj klucza oznacza sukces. Ten rozmiar obejmuje miejsce dla terminator o wartości null.  
  
 Wartość zero wskazuje błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError` funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `cchSrc` jest większa od zera i `lpSrcStr` jest ciąg zakończony znakiem null `__crtLCMapStringW` ustawia `cchSrc` do długości ciągu. Następnie `__crtLCMapStringW` wywołuje szerokiego ciągu (Unicode) wersję `LCMapString` funkcji z określonymi parametrami. Aby uzyskać więcej informacji na temat parametrów i wartość zwracana przez tę funkcję, zobacz [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__crtLCMapStringW|awint.h|