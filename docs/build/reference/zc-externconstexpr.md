---
title: '/ Zc: externconstexpr (Włącz zmienne extern constexpr) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac52c073135ecc88536b6aaa2beee7308ba53b9c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419129"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/ Zc: externconstexpr (Włącz zmienne extern constexpr)

**/Zc: externconstexpr** — opcja kompilatora informuje kompilator, aby przestrzegać standardu C++ i pozostawić powiązania zewnętrzne dla `constexpr` zmiennych. Domyślnie, program Visual Studio zawsze zapewnia `constexpr` zmiennej wewnątrz powiązania, nawet jeśli określisz `extern` — słowo kluczowe.

## <a name="syntax"></a>Składnia

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Uwagi

**/Zc: externconstexpr** — opcja kompilatora powoduje, że kompilator dotyczą zmienne zadeklarowane za pomocą zewnętrznego powiązania `extern constexpr`. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc:externConstexpr-** jest określony, program Visual Studio stosuje zewnętrzne do `constexpr` nawet wtedy, gdy zmienne `extern` słowo kluczowe jest używane. **/Zc: externconstexpr** opcja jest dostępna, począwszy od wersji 15.6 programu Visual Studio 2017 Update. i jest domyślnie wyłączona. [/ Permissive-](permissive-standards-conformance.md) opcji nie włącza **/Zc: externconstexpr**.

Jeśli nagłówek pliku zawiera zmiennej zadeklarowanej `extern constexpr`, muszą być oznaczone [__declspec(selectany)](../../cpp/selectany.md) w celu scalenia deklaracji zduplikowanych pojedynczego wystąpienia w połączonych danych binarnych. W przeciwnym razie mogą pojawić się błędy konsolidatora, na przykład LNK2005 dla naruszenia reguły jednej definicji.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **/Zc: externconstexpr** lub **/Zc:externConstexpr-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz też

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)