---
title: clog, clogf, clogl
ms.date: 11/04/2016
apiname:
- clog
- clogf
- clogl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: fcbc9ba7984898d51f7a3d0beb5ef7c8b6d6892c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340641"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Pobiera logarytm naturalny liczby zespolonej z gałęzią Wytnij rzeczywistych osi ujemna.

## <a name="syntax"></a>Składnia

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Podstawa logarytmu.

## <a name="return-value"></a>Wartość zwracana

Logarytm naturalny *z*. Wynik jest nieograniczona, wzdłuż osi rzeczywiste, a w interwale [-iπ, + iπ] urojone osi.

Możliwe wartości zwracane są:

|Parametr z|Wartość zwracana|
|-----------------|------------------|
|Dodatnie|Logarytm 10 z|
|Zero|- ∞|
|Ujemne|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **clog —** przyjmujące i zwracające **_Fcomplex** i **_Lcomplex** wartości. W programie C **clog —** zawsze przyjmuje i zwraca **_Dcomplex** wartości.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**clog —**, **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
