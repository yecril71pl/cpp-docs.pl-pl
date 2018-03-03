---
title: "/Zc:externConstexpr (Włącz extern constexpr zmienne) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84037e5e8a942d51175d97957d0c05bd6f4aa29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr (Włącz extern constexpr zmienne)

**/Zc:externConstexpr** — opcja kompilatora informuje kompilator, aby być zgodne ze standardem C++ i Zezwalaj na połączenie zewnętrzne dla `constexpr` zmiennych. Domyślnie zawsze daje Visual Studio `constexpr` zmiennej połączenie wewnętrzne, nawet jeśli określisz `extern` — słowo kluczowe.

## <a name="syntax"></a>Składnia

> /Zc:externConstexpr [-]

## <a name="remarks"></a>Uwagi

**/Zc:externConstexpr** — opcja kompilatora powoduje, że kompilator dotyczą połączenie zewnętrzne zmiennych zadeklarowano za pomocą `extern constexpr`. **/Zc:externConstexpr** opcja jest dostępna w programie Visual Studio 2017 aktualizacji 15,5 cala. We wcześniejszych wersjach programu Visual Studio i domyślnie lub, jeśli **/Zc:externConstexpr-** jest określony, program Visual Studio stosuje zewnętrzne do `constexpr` zmienne, nawet jeśli `extern` słowo kluczowe jest używane.

Jeśli plik nagłówka zawiera Zmienna zadeklarowana `extern constexpr`, muszą być oznaczone jako [__declspec(selectany)](../../cpp/selectany.md) Aby scalić zduplikowane deklaracje pojedynczego wystąpienia w połączonych danych binarnych. W przeciwnym razie mogą zostać wyświetlone błędy konsolidatora, na przykład LNK2005 dla naruszenia reguły jednej definicji.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** , a następnie wybierz **wiersza polecenia**.

1. Dodaj **/Zc:externConstexpr** lub **/Zc:externConstexpr-** do **dodatkowe opcje:** okienka.

## <a name="see-also"></a>Zobacz też

[/Zc (zgodność)](../../build/reference/zc-conformance.md)  
[Auto, słowo kluczowe](../../cpp/auto-keyword.md)