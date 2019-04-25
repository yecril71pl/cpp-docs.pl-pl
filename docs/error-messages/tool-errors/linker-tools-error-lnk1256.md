---
title: Błąd narzędzi konsolidatora LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: 47c20f24a2fe26cc96d5efcf359652a40af508ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160578"
---
# <a name="linker-tools-error-lnk1256"></a>Błąd narzędzi konsolidatora LNK1256

Operacja ALINK nie powiodła się: Przyczyna

Typową przyczyną LNK1256 jest nieprawidłowy numer wersji dla zestawu. Wartość 65535 nie jest dozwolona dla dowolnej części numeru wersji zestawu. Prawidłowy zakres dla wersji zestawu to 0 - 65534.

Również może być spowodowany LNK1256, jeśli ALINK nie można odnaleźć nazwanego kontenera kluczy. Usuwanie kontenera kluczy i dodaj go ponownie do CSP silnej nazwy przy użyciu [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Inną przyczyną LNK1256 niezgodność wersji między konsolidatora i Alink.dll. Przyczyną może być uszkodzenie instalacji programu Visual Studio. Użyj **programy i funkcje** w Panelu sterowania Windows, aby naprawić lub zainstalować ponownie program Visual Studio.

Poniższy przykład spowoduje wygenerowanie LNK1256:

```
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```