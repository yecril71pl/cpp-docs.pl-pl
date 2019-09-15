---
title: _RPT, _RPTF, _RPTW, _RPTFW — Makra
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 567fe0a68f5adad6f5d90ef3da9d673a75bb83a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949085"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW — Makra

Śledzi postęp aplikacji przez wygenerowanie raportu debugowania (tylko wersja do debugowania). Należy zauważyć, że *n* określa liczbę argumentów w *args* i może mieć wartość 0, 1, 2, 3, 4 lub 5.

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
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**lub **_CRT_ASSERT**.

*format*<br/>
Ciąg sterujący formatem użyty do utworzenia komunikatu użytkownika.

*argumentów*<br/>
Argumenty podstawienia używane przez *Format*.

## <a name="remarks"></a>Uwagi

Wszystkie te makra przyjmują parametry *reportType* i *Format* . Ponadto mogą one także przyjmować do czterech dodatkowych argumentów oznaczonych liczbą dołączoną do nazwy makra. Na przykład **_RPT0** i **_RPTF0** nie przyjmują żadnych dodatkowych argumentów, **_RPT1** i **_RPTF1** przyjmują *arg1*, **_RPT2** i **_RPTF2** przyjmują *arg1* i **arg2**i tak dalej.

Makra **_RPT** i **_RPTF** są podobne do funkcji [printf](printf-printf-l-wprintf-wprintf-l.md) , ponieważ mogą służyć do śledzenia postępu aplikacji podczas procesu debugowania. Jednak te makra są bardziej elastyczne niż **printf** , ponieważ nie muszą być ujęte w instrukcje **#ifdef** , aby uniemożliwić ich wywoływanie w kompilacji detalicznej aplikacji. Tę elastyczność uzyskuje się za pomocą makra [_DEBUG](../../c-runtime-library/debug.md) ; makra **_RPT** i **_RPTF** są dostępne tylko wtedy, gdy flaga **_DEBUG** jest zdefiniowana. Gdy **_DEBUG** nie jest zdefiniowany, wywołania tych makr są usuwane podczas przetwarzania wstępnego.

Makra **_RPTW** i **_RPTFW** są wersjami znaków dwubajtowych tych makr. Są one takie jak **wprintf** i pobierają ciągi znaków dwubajtowych jako argumenty.

Makra **_RPT** wywołują funkcję [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) w celu wygenerowania raportu debugowania z komunikatem użytkownika. Makra **_RPTW** wywołują funkcję **_CrtDbgReportW** , aby generować ten sam raport z szeroką literą. Makra **_RPTF** i **_RPTFW** umożliwiają utworzenie raportu debugowania zawierającego plik źródłowy i numer wiersza, w którym zostało wywołane makro raportu, poza komunikatem użytkownika. Komunikat użytkownika jest tworzony przez podstawianie argumentów **ARG**[*n*] do ciągu *formatu* , przy użyciu tych samych reguł zdefiniowanych przez funkcję [printf](printf-printf-l-wprintf-wprintf-l.md) .

**_CrtDbgReport** lub **_CrtDbgReportW** generuje raport debugowania i określa jego lokalizacje docelowe w oparciu o bieżące tryby raportu i plik zdefiniowany dla elementu *reportType*. Funkcje [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) służą do definiowania miejsc docelowych dla każdego typu raportu.

Jeśli wywoływane jest makro **_RPT** , a nie **_CrtSetReportMode** ani **_CrtSetReportFile** , komunikaty są wyświetlane w następujący sposób.

|Typ raportu|Miejsce docelowe danych wyjściowych|
|-----------------|------------------------|
|**_CRT_WARN**|Tekst ostrzeżenia nie jest wyświetlany.|
|**_CRT_ERROR**|Okno podręczne. Analogicznie jak `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` gdyby zostały określone.|
|**_CRT_ASSERT**|Analogicznie jak **_CRT_ERROR**.|

Gdy lokalizacja docelowa jest oknem komunikatu debugowania, a użytkownik wybierze przycisk **Ponów próbę** , **_CrtDbgReport** lub **_CrtDbgReportW** zwraca wartość 1, powodując, że te makra uruchamiają debuger, pod warunkiem, że włączone jest debugowanie just-in-Time (JIT). Aby uzyskać więcej informacji na temat używania tych makr jako mechanizmu obsługi błędów debugowania, zobacz [Używanie makr do weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).

Istnieją dwa inne makra, które generują raport debugowania. Makro [_ASSERT](assert-asserte-assert-expr-macros.md) generuje raport, ale tylko wtedy, gdy jego argument expression ma wartość false. [_ASSERTE](assert-asserte-assert-expr-macros.md) jest dokładnie taki sam jak **_ASSERT**, ale zawiera wyrażenie zakończone niepowodzeniem w wygenerowanym raporcie.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|Makra **_RPT**|\<crtdbg.h>|
|Makra **_RPTF**|\<crtdbg.h>|
|Makra **_RPTW**|\<crtdbg.h>|
|Makra **_RPTFW**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

Mimo że są to makra i są uzyskiwane przez włączenie CRTDBG. h, aplikacja musi łączyć się z jedną z bibliotek debugowania, ponieważ te makra wywołują inne funkcje w czasie wykonywania.

## <a name="example"></a>Przykład

Zobacz przykład w temacie [_ASSERT](assert-asserte-assert-expr-macros.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
