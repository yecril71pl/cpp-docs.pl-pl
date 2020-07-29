---
title: /Zc:externConstexpr (Włącz zmienne extern constexpr)
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 7546ab6d81137a2abb053cd18f0d5d74913c3b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211908"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr`(Włącz zmienne constexpr extern)

**`/Zc:externConstexpr`** Opcja kompilatora instruuje kompilator, aby był zgodny ze standardem C++ i zezwala na zewnętrzne powiązanie dla **`constexpr`** zmiennych. Domyślnie program Visual Studio zawsze zapewnia **`constexpr`** zmienny związek wewnętrzny, nawet w przypadku określenia **`extern`** słowa kluczowego.

## <a name="syntax"></a>Składnia

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>Uwagi

**`/Zc:externConstexpr`** Opcja kompilatora powoduje, że kompilator zastosuje zewnętrzne połączenie ze zmiennymi zadeklarowanymi przy użyciu `extern constexpr` . We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **`/Zc:externConstexpr-`** jest określona, program Visual Studio stosuje wewnętrzne połączenie ze **`constexpr`** zmiennymi, nawet jeśli **`extern`** słowo kluczowe jest używane. Ta **`/Zc:externConstexpr`** opcja jest dostępna, zaczynając od programu Visual Studio 2017 Update 15,6. i jest domyślnie wyłączona. [`/permissive-`](permissive-standards-conformance.md)Opcja nie jest włączona **`/Zc:externConstexpr`** .

Jeśli plik nagłówkowy zawiera zmienną zadeklarowaną `extern constexpr` , należy ją oznaczyć [`__declspec(selectany)`](../../cpp/selectany.md) w celu scalenia zduplikowanych deklaracji w jedno wystąpienie w połączonym pliku binarnym. W przeciwnym razie można zobaczyć błędy konsolidatora, na przykład LNK2005, w przypadku naruszeń reguły z jedną definicją.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Dodaj **`/Zc:externConstexpr`** lub **`/Zc:externConstexpr-`** do **opcji dodatkowe:** okienko.

## <a name="see-also"></a>Zobacz także

[`/Zc`Zgodności](zc-conformance.md)<br/>
[`auto`Kodu](../../cpp/auto-keyword.md)
