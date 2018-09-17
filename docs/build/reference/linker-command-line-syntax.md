---
title: Składnia wiersza polecenia konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f1e891d91b96c5f29fb01dae5b1b8b9d731cdf3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718350"
---
# <a name="linker-command-line-syntax"></a>Składnia wiersza polecenia konsolidatora

Aby uruchomić łącza. Plik EXE, należy użyć następującej składni polecenia:

```
LINK arguments
```

`arguments` Obejmują opcje i nazwy plików i może być określony w dowolnej kolejności. Dostępne są opcje przetwarzania pierwsze, następnie pliki. Użyj miejsc do magazynowania lub karty do oddzielenia argumentów.

> [!NOTE]
>  To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

W wierszu polecenia opcję składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), a następnie Nazwa opcji. Nie należy skracać nazwy opcji. Niektóre opcje przyjmować argument, określone po dwukropek (:). Nie spacje lub tabulatory są dozwolone w obrębie Specyfikacja opcji z wyjątkiem w ciąg w cudzysłowie w opcji/Comment. Określ argumenty liczbowe w wartości dziesiętne lub notacji języka C. Nie jest uwzględniana wielkość liter nazw opcji oraz ich argumentach — słowo kluczowe lub nazwę pliku, ale identyfikatorów jako argumentów jest uwzględniana wielkość liter.

Aby przekazać plik do konsolidatora, określ nazwę pliku w wierszu polecenia po poleceniu łącza. Można określić ścieżkę bezwzględną lub względną z nazwę pliku i można używać symboli wieloznacznych w nazwie pliku. Jeśli zostanie pominięty, kropki (.) i rozszerzenie nazwy pliku, łącze przyjęto założenie, .obj, w celu znajdowania plików. ŁĄCZE nie używa rozszerzenia nazw plików lub brak ich się założeń dotyczących zawartości plików. Określa typ pliku, badając ją i przetwarza je w związku z tym.

Link.exe zwraca 0 w przypadku sukcesu (bez błędów).  W przeciwnym razie program łączący zwraca numer błędu, który zatrzymał łącze.  Na przykład jeśli konsolidator wygeneruje LNK1104, konsolidator zwraca 1104.  W związku z tym najniższy numer błędu zwracany w przypadku błędu przez konsolidator wynosi 1000.  Zwracana wartość wynosząca 128 reprezentuje na problem z konfiguracją systemu operacyjnego lub pliku .config; Moduł ładujący nie została załadowana link.exe lub c2.dll.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)