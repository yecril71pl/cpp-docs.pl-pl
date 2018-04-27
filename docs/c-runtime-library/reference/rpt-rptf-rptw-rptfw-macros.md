---
title: _RPT, _RPTF, _RPTW, _rptfw — makra | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1692789ff2dac85e6ca33aa6b05ced6a01f30cba
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW — Makra

Śledzi postęp aplikacji przez Generowanie raportu debugowania (tylko wersja do debugowania). Należy pamiętać, że *n* określa liczbę argumentów *argumentów* i może być 0, 1, 2, 3, 4 i 5.

## <a name="syntax"></a>Składnia

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>Parametry

*reportType* typ raportu: **_CRT_WARN**, **_CRT_ERROR**, lub **_CRT_ASSERT**.

*Format* ciąg formatu kontroli używany do tworzenia komunikatów użytkownika.

*argumenty* Podstawienie argumentów używana przez *format*.

## <a name="remarks"></a>Uwagi

Te makra zająć *reportType* i *format* parametrów. Ponadto one może potrwać maksymalnie cztery dodatkowe argumenty oznaczony numerem dodanym na końcu nazwy makra. Na przykład **_rpt0 —** i **_rptf0 —** nie wymaga żadnych dodatkowych argumentów **_rpt1 —** i **_rptf1 —** zająć *arg1*, **_Rpt2 —** i **_rptf2 —** zająć *arg1* i **arg2**i tak dalej.

**_RPT** i **_RPTF** makra są podobne do [printf](printf-printf-l-wprintf-wprintf-l.md) działać, ponieważ może służyć do śledzić postęp aplikacji podczas debugowania. Jednak te makra są bardziej elastyczne niż **printf** ponieważ nie muszą być ujęte w **#ifdef** instrukcje, aby uniemożliwić ich wywołana w sprzedaży detalicznej kompilacji aplikacji. Tego rodzaju elastyczności jest realizowane za pośrednictwem [_DEBUG](../../c-runtime-library/debug.md) makro; **_RPT** i **_RPTF** makra są dostępne tylko podczas **_DEBUG** flaga jest zdefiniowane. Gdy **_DEBUG** jest niezdefiniowana, wywołań do tych makr są usuwane podczas przetwarzania wstępnego.

**_RPTW** i **_rptfw —** makra są wersje tych makr znaków dwubajtowych. Są one podobne **wprintf** i pobierają ciągi znaków dwubajtowych jako argumenty.

**_RPT** wywołanie makra [_crtdbgreport —](crtdbgreport-crtdbgreportw.md) funkcji, aby wygenerować raport debugowania z następującym komunikatem użytkownika. **_RPTW** wywołanie makra **_crtdbgreportw —** funkcji do generowania jednym raporcie z znaki dwubajtowe. **_RPTF** i **_rptfw —** makra utworzyć raport debugowania z liczbą plików i wierszy źródła gdzie makro raportu została wywołana, oprócz komunikat użytkownika. Zostanie utworzony komunikat użytkownika, zastępując **arg**[*n*] argumenty do *format* ciąg znaków, według reguł zdefiniowanych przez [printf](printf-printf-l-wprintf-wprintf-l.md)funkcji.

**_Crtdbgreport —** lub **_crtdbgreportw —** generuje raport debugowania i określa jej miejsc docelowych oparte na trybie Bieżące raportu i plik zdefiniowane dla *reportType*. [_Crtsetreportmode —](crtsetreportmode.md) i [_crtsetreportfile —](crtsetreportfile.md) funkcje są używane do definiowania miejsc docelowych dla każdego typu raportu.

Jeśli **_RPT** nosi nazwę makra i ani **_crtsetreportmode —** ani **_crtsetreportfile —** została wywołana, komunikaty są wyświetlane w następujący sposób.

|Typ raportu|Miejsce docelowe danych wyjściowych|
|-----------------|------------------------|
|**_CRT_WARN**|Tekst ostrzeżenia nie są wyświetlane.|
|**_CRT_ERROR**|Okno podręczne. Tym samym tak, jakby `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` jakby określono.|
|**_CRT_ASSERT**|Taki sam jak **_CRT_ERROR**.|

Gdy obiektem docelowym jest oknem komunikatu debugowania i użytkownik wybierze **ponów** przycisku **_crtdbgreport —** lub **_crtdbgreportw —** zwraca wartość 1 powoduje tych makr uruchomić Debuger, pod warunkiem, że włączone jest debugowanie programu just in time (JIT). Aby uzyskać więcej informacji o używaniu tych makr jako mechanizmu obsługi debugowania błąd, zobacz [przy użyciu makra weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).

Istnieją dwa inne makra, które Generowanie raportu debugowania. [_ASSERT](assert-asserte-assert-expr-macros.md) makro generuje raport, ale tylko wtedy, gdy jej argument wyrażenie daje w wyniku wartość FALSE. [_Asserte —](assert-asserte-assert-expr-macros.md) jest dokładnie podobnego **_ASSERT**, ale zawiera wyrażenie, które nie powiodło się w generowanym raporcie.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|**_RPT** makra|\<crtdbg.h>|
|**_RPTF** makra|\<crtdbg.h>|
|**_RPTW** makra|\<crtdbg.h>|
|**_Rptfw —** makra|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

Mimo że te są makra i są pobierane przez dołączenie Crtdbg.h, aplikacja musi połączyć z jednej z bibliotek debugowania, ponieważ tych makr wywołaniem innych funkcji środowiska wykonawczego.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_ASSERT](assert-asserte-assert-expr-macros.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
