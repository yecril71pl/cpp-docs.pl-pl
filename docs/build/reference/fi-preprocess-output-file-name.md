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
ms.openlocfilehash: 990c48a72c3f6017d893ddf9b46bcbb737bfb634
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820198"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)

Określa nazwę pliku wyjściowego, do którego [/P (Przetwarzaj wstępnie do pliku)](p-preprocess-to-a-file.md) — opcja kompilatora zapisuje wstępnie przetworzone produkty wyjściowe.

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

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[/P (Przetwarzaj wstępnie do pliku)](p-preprocess-to-a-file.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
