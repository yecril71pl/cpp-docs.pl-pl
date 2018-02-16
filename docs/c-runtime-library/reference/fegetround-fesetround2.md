---
title: fegetround, fesetround2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
dev_langs:
- C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf50371c781a5ade76f3f35de8fc760331d72a20
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround
Pobiera lub ustawia bieżący tryb zaokrąglania liczb zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `round_mode`  
 Tryb zaokrąglania można ustawić jako jeden zmiennoprzecinkowe makra zaokrąglania. Jeśli wartość nie jest równa jeden zmiennoprzecinkowe zaokrąglania makra, trybu zaokrąglania nie ulega zmianie.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `fegetround` zwraca tryb zaokrąglania wśród zmiennoprzecinkowej zaokrąglanie wartości makra. Zwraca wartość ujemną, jeśli nie można określić bieżącego trybu zaokrąglania.  
  
 W przypadku powodzenia `fesetround` zwraca wartość 0. W przeciwnym razie jest zwracana wartość inną niż zero.  
  
## <a name="remarks"></a>Uwagi  
 Zmiennoprzecinkowe operacje można użyć jednego z kilku trybów zaokrąglania. Te kontrolować kierunek, w którym są zaokrąglane wyniki operacji zmiennoprzecinkowej kierunku, gdy wyniki są przechowywane. Są to nazwy i zachowania zmiennoprzecinkowego zaokrąglania makra zdefiniowane w \<fenv.h >:  
  
|Macro|Opis|  
|-----------|-----------------|  
|FE_DOWNWARD|Zaokrąglij do nieskończoności ujemnej.|  
|FE_TONEAREST|Zaokrąglij do najbliższej.|  
|FE_TOWARDZERO|Zaokrąglij w kierunku zera.|  
|FE_UPWARD|Zaokrąglij do nieskończoności dodatniej.|  
  
 Domyślne zachowanie FE_TONEAREST jest zaokrąglona połowie wyników między można przedstawić wartości do najbliższej wartości z nawet (0) bitem.  
  
 Bieżący tryb zaokrąglania ma wpływ na następujące operacje:  
  
-   Ciąg konwersji.  
  
-   Wyniki zmiennoprzecinkowe operatorów arytmetycznych poza wyrażenia stałe.  
  
-   Biblioteka zaokrąglania funkcje, takie jak `rint` i `nearbyint`.  
  
-   Wartości zwracane z biblioteki standardowej funkcji matematycznych.  
  
 Bieżący tryb zaokrąglania nie ma wpływu na te operacje:  
  
-   `trunc`, `ceil`, `floor`, I `lround` funkcji biblioteki.  
  
-   Zmiennoprzecinkowe do liczby całkowitej niejawnego rzutowania i konwersje, które zawsze zaokrąglona w kierunku zera.  
  
-   Wyniki zmiennoprzecinkowe operatorów arytmetycznych w stałych wyrażeń, które zawsze zaokrąglona do najbliższej wartości.  
  
 Aby korzystać z tych funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fegetround`,                `fesetround`|\<fenv.h>|\<cfenv>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint —, nearbyintf —, nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)