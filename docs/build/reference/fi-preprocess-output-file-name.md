---
title: /Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: d4de722ad33a9c9e5e7c37176bbe5d7031b68a39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450183"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)

Określa nazwę pliku wyjściowego, do którego [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora zapisuje wstępnie przetworzone produkty wyjściowe.

## <a name="syntax"></a>Składnia

```
/Fipathname
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pathname`|Nazwa i ścieżka pliku wyjściowego produkowane przez **/P** — opcja kompilatora.|

## <a name="remarks"></a>Uwagi

Użyj **/Fi** — opcja kompilatora w połączeniu z **/P** — opcja kompilatora.

Jeśli określisz tylko ścieżka dla `pathname` parametru podstawowej nazwy pliku źródłowego jest używana jako nazwa podstawowa pliku wstępnie przetworzone produkty wyjściowe. `pathname` Parametr nie jest wymagane rozszerzenie nazwy pliku określonej. Jednak rozszerzenie ".i" jest używana, jeśli nie określisz rozszerzenie nazwy pliku.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu wstępnie przetwarza PROGRAM.cpp, zachowuje komentarze, dodaje [#line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektyw i zapisuje wynik w pliku MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)