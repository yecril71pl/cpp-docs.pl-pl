---
title: spectre | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b515d25d4818cf8b6213a37f3fe78df4f3882a69
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
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
