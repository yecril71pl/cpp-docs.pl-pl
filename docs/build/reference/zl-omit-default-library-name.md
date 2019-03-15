---
title: /Zl (Pomiń domyślną nazwę biblioteki)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: cb8083d874abe17add1d27096ebce143d03a04cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809590"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Pomiń domyślną nazwę biblioteki)

Pomija domyślną nazwę biblioteki środowiska uruchomieniowego języka C z pliku .obj. Domyślnie kompilator umieszcza nazwę biblioteki z pliku .obj, aby nakazać konsolidator odpowiedniej biblioteki.

## <a name="syntax"></a>Składnia

```
/Zl
```

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat domyślnej biblioteki, zobacz [korzystaj z bibliotek wykonawczych](md-mt-ld-use-run-time-library.md).

Możesz użyć **/Zl** do kompilowania plików .obj, które ma być umieszczony w bibliotece. Mimo że pomijając nazwę biblioteki zapisuje tylko małej ilości miejsca dla pliku obj pojedynczy, całkowita ilość miejsca, zapisane jest znaczący bibliotekę, która zawiera wiele modułów obiektu.

Ta opcja jest to opcja zaawansowana. Ustawienie tej opcji spowoduje usunięcie niektórych Obsługa bibliotek środowiska uruchomieniowego C, które mogą być wymagane przez aplikację, co powoduje błędy w czasie konsolidacji w przypadku aplikacji zależy od tej obsługi. Jeśli używasz tej opcji należy podać wymagane składniki w inny sposób.

Użyj [/nodefaultlib (Ignoruj biblioteki)](nodefaultlib-ignore-libraries.md). Aby nakazać konsolidator, aby zignorować odwołań do biblioteki we wszystkich plikach .obj.

Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

Podczas kompilowania za pomocą **/Zl**, `_VC_NODEFAULTLIB` jest zdefiniowana.  Na przykład:

```
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Pomiń domyślne nazwy bibliotek** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
