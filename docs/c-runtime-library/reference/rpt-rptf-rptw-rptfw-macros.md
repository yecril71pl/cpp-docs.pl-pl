---
title: _RPT, _RPTF, _RPTW, _rptfw — makra | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69347ab698661346b8d598dda1bb007d071a21f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104150"
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW — Makra

Aplikacja postęp jest śledzony przez wygenerowanie raportu debugowania (tylko wersja debugowania). Należy pamiętać, że *n* określa liczbę argumentów *args* i może być 0, 1, 2, 3, 4 lub 5.

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

*reportType*<br/>
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**, lub **_CRT_ASSERT**.

*Format*<br/>
Ciąg formantu formatu używany do tworzenia wiadomości użytkownika.

*argumenty*<br/>
Argumenty podstawiania używane przez *format*.

## <a name="remarks"></a>Uwagi

Wszystkie te makra nie przyjmują *reportType* i *format* parametrów. Ponadto ich może zająć maksymalnie cztery dodatkowe argumenty oznaczona liczba dołączana do nazwy makra. Na przykład **_RPT0** i **_RPTF0** nie wymaga żadnych dodatkowych argumentów **_RPT1** i **_RPTF1** zająć *arg1*, **_RPT2** i **_RPTF2** zająć *arg1* i **argument2**i tak dalej.

**_RPT** i **_RPTF** makra są podobne do [printf](printf-printf-l-wprintf-wprintf-l.md) działać, ponieważ może służyć do śledzenia postępu aplikacji podczas debugowania procesu. Jednak te makra są bardziej elastyczne niż **printf** ponieważ nie muszą być ujęte w nawiasy **#ifdef** instrukcji, aby uniemożliwić ich wywoływana w przypadku kompilacji detalicznej aplikacji. Ta elastyczność to osiągnąć, używając [_DEBUG](../../c-runtime-library/debug.md) — makro; **_RPT** i **_RPTF** makra są dostępne tylko w przypadku **_DEBUG** flaga jest zdefiniowane. Gdy **_DEBUG** jest nie jest zdefiniowany, wywołania te makra są usuwane podczas przetwarzania wstępnego.

**_RPTW** i **_rptfw —** makra są wersjami znaków dwubajtowych tych makr. Są one podobne **wprintf** i ciągi znaków dwubajtowych jako argumenty.

**_RPT** wywołanie makra [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) funkcję, aby wygenerować raport debugowania z komunikatem użytkownika. **_RPTW** wywołanie makra **_crtdbgreportw —** funkcję, aby wygenerować ten sam raport przy użyciu znaków dwubajtowych. **_RPTF** i **_rptfw —** makra utworzony raport debugowania ze źródłowego pliku i numer wiersza gdzie makro raportu została wywołana, dodatkowo do dla użytkownika komunikat o. Dla użytkownika komunikat o utworzeniu wstawiając **arg**[*n*] argumenty do *format* ciąg znaków, przy użyciu tych samych zasad zdefiniowanych przez [printf](printf-printf-l-wprintf-wprintf-l.md)funkcji.

**_CrtDbgReport** lub **_crtdbgreportw —** generuje raport debugowania i określa jej miejsc docelowych w oparciu o bieżące tryby raportów i plik zdefiniowany dla *reportType*. [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) funkcje są używane do definiowania miejsca docelowe dla każdego typu raportu.

Jeśli **_RPT** nosi nazwę makra a **_CrtSetReportMode** ani **_CrtSetReportFile** została wywołana, komunikaty są wyświetlane w następujący sposób.

|Typ raportu|Miejsce docelowe danych wyjściowych|
|-----------------|------------------------|
|**_CRT_WARN**|Tekst ostrzeżenia nie są wyświetlane.|
|**_CRT_ERROR**|Okno podręczne. Tym samym tak, jakby `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` jakby określono.|
|**_CRT_ASSERT**|Taki sam jak **_CRT_ERROR**.|

Jeśli miejsce docelowe jest okna komunikatów debugowania i użytkownik wybierze **ponów próbę wykonania** przycisku **_CrtDbgReport** lub **_crtdbgreportw —** zwraca wartość 1, co powoduje tych makr rozpocząć debugera, pod warunkiem, że włączone jest debugowanie programu just-in-time (JIT). Aby uzyskać więcej informacji o używaniu tych makr, jako mechanizm obsługi błędów debugowania, zobacz [używania makr do weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).

Dwa inne makra istnieje, które generują raport debugowania. [_ASSERT](assert-asserte-assert-expr-macros.md) — makro generuje raport, ale tylko wtedy, gdy jej argument wyrażenie zwróci wartość FALSE. [_Asserte —](assert-asserte-assert-expr-macros.md) jest dokładnie like **_ASSERT**, ale zawiera wyrażenie zakończonych niepowodzeniem w wygenerowanym raporcie.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|**_RPT** makra|\<crtdbg.h>|
|**_RPTF** makra|\<crtdbg.h>|
|**_RPTW** makra|\<crtdbg.h>|
|**_Rptfw —** makra|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

Mimo że te makra są i są pobierane przez dołączenie Crtdbg.h, aplikacja musi łączyć przy użyciu jednej z bibliotek debugowania, ponieważ te makra wywołania innych funkcji wykonawczej.

## <a name="example"></a>Przykład

Zobacz przykład w [_ASSERT](assert-asserte-assert-expr-macros.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
