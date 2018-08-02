---
title: luki spectre | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a51d47764ea4515fcbc2cb3b7aa37fd341cd130e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463232"
---
# <a name="spectre"></a>luki spectre

**Microsoft Specific**

Informuje kompilator, aby nie wstawiać luki Spectre w wariancie 1 związanego z wykonywaniem spekulatywnym barierę instrukcje dla funkcji.

## <a name="syntax"></a>Składnia

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Uwagi

[/Qspectre](../build/reference/qspectre.md) — opcja kompilatora powoduje, że kompilator wstawić związanego z wykonywaniem spekulatywnym barierę instrukcje, gdzie analizy oznacza, że istnieje luka w zabezpieczeniach Spectre w wariancie 1. Szczegółowe instrukcje, które są emitowane zależeć od procesora. Chociaż te instrukcje mają minimalny wpływ na rozmiar kodu lub wydajności, może to być przypadkach, gdy kod nie dotyczy luki w zabezpieczeniach i wymaga maksymalną wydajność.

Analiza eksperta może określić, że funkcja jest pozbawione luki Spectre w wariancie 1 granice wyboru obejścia wadę. W takim przypadku można pominąć generowanie kodu środki zaradcze w funkcji, stosując `__declspec(spectre(nomitigation))` przy deklaracji funkcji.

> [!CAUTION]
> **/Qspectre** instrukcje barierę związanego z wykonywaniem spekulatywnym zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także
 [__declspec](../cpp/declspec.md)  
 [Słowa kluczowe](../cpp/keywords-cpp.md)  
 [/Qspectre](../build/reference/qspectre.md)  
