---
title: '/ Zc: externconstexpr (Włącz zmienne extern constexpr)'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 3c18a5310646ea39c0599f709e9fddc3990b7a2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315758"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/ Zc: externconstexpr (Włącz zmienne extern constexpr)

**/Zc: externconstexpr** — opcja kompilatora informuje kompilator, aby przestrzegać standardu C++ i pozostawić powiązania zewnętrzne dla `constexpr` zmiennych. Domyślnie, program Visual Studio zawsze zapewnia `constexpr` zmiennej wewnątrz powiązania, nawet jeśli określisz `extern` — słowo kluczowe.

## <a name="syntax"></a>Składnia

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Uwagi

**/Zc: externconstexpr** — opcja kompilatora powoduje, że kompilator dotyczą zmienne zadeklarowane za pomocą zewnętrznego powiązania `extern constexpr`. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc:externConstexpr-** jest określony, program Visual Studio stosuje zewnętrzne do `constexpr` nawet wtedy, gdy zmienne `extern` słowo kluczowe jest używane. **/Zc: externconstexpr** opcja jest dostępna, począwszy od wersji 15.6 programu Visual Studio 2017 Update. i jest domyślnie wyłączona. [/ Permissive-](permissive-standards-conformance.md) opcji nie włącza **/Zc: externconstexpr**.

Jeśli nagłówek pliku zawiera zmiennej zadeklarowanej `extern constexpr`, muszą być oznaczone [__declspec(selectany)](../../cpp/selectany.md) w celu scalenia deklaracji zduplikowanych pojedynczego wystąpienia w połączonych danych binarnych. W przeciwnym razie mogą pojawić się błędy konsolidatora, na przykład LNK2005 dla naruszenia reguły jednej definicji.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **/Zc: externconstexpr** lub **/Zc:externConstexpr-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
