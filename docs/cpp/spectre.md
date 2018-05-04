---
title: spectre | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 153ff690b975ecb442c260fcebce73acd32d03fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="spectre"></a>spectre

**Microsoft Specific**

Informuje kompilator, nie można wstawić Spectre wariantu 1 rozważana wykonywania bariery instrukcje dotyczące funkcji.

## <a name="syntax"></a>Składnia

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Uwagi

[/Qspectre](../build/reference/qspectre.md) — opcja kompilatora powoduje, że kompilator, aby wstawić rozważana wykonywania instrukcji bariery, gdzie analizy wskazuje, że istnieje luka w zabezpieczeniach wariantu 1 Spectre. Szczegółowe instrukcje wysyłanego zależy od procesora. Gdy te instrukcje ma minimalny wpływ na rozmiar kodu lub wydajności, może być przypadkach, gdy nie ma wpływu na usterkę kodu i wymaga maksymalną wydajność.

Ekspert analizy może określić, że funkcja jest przed defektu Spectre wariantu 1 granice wyboru obejścia. W takim przypadku można pominąć generowanie kodu środki zaradcze w funkcji, stosując `__declspec(spectre(nomitigation))` do deklaracji funkcji.

> [!CAUTION]
> **/Qspectre** rozważana wykonywania instrukcji bariery udostępniają ważne zabezpieczenia i mieć nieznaczny wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia `__declspec(spectre(nomitigation))`.

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
