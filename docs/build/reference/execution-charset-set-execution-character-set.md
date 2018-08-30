---
title: — wykonanie-charset (Ustaw zestaw znaków wykonywania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02f3e4273e9fc4064b26c6e32d708c4e6d586ae1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212675"
---
# <a name="execution-charset-set-execution-character-set"></a>/ Execution-Charset (Ustaw zestaw znaków wykonywania)
Umożliwia określenie zestawu dla Twojego pliku wykonywalnego znaków wykonania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Argumenty  
 **IANA_name**  
 Nazwa zestawu znaków zdefiniowanych przez organizację IANA.  
  
 **CPID**  
 Identyfikator strony kodu.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć **/Execution-Charset** opcję, aby określić zestaw znaków wykonania. Zestaw znaków wykonania jest kodowanie używane do tekstu programu, która jest wprowadzana do fazy kompilacji po wszystkich przetwarzania wstępnego kroki. Zestaw znaków jest używany do wewnętrznej reprezentacji dowolnego ciąg lub znak literałów w skompilowanym kodzie. Ustaw tę opcję, aby określić wykonania rozszerzonego zestawu znaków do użycia podczas plików źródłowych zawierają znaki, które nie są reprezentowanych w zestaw znaków wykonania podstawowego. Możesz użyć albo organizację IANA nazwy zestawu znaków ISO lub pojedynczego znaku kropki (.), a następnie przez identyfikator 3 – 5 cyfr kodu dziesiętnego strony, aby określić używany zestaw znaków. Aby uzyskać listę obsługiwanych identyfikatorami stronę kodu i nazwy zestawu znaków, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).  
  
 Domyślnie program Visual Studio wykrywa znacznika kolejności bajtów, aby określić, czy plik źródłowy jest w formacie zakodowanym Unicode, na przykład, UTF-16 lub UTF-8. Jeśli zostanie znaleziony Brak znacznika kolejności bajtów, zakłada się pliku źródłowego jest zakodowane przy użyciu bieżącej stronie kodowej użytkownika, chyba że określono nazwę lub kod strony zbiór znaków za pomocą **/Source-Charset** opcji lub **/UTF-8** opcji. Program Visual Studio umożliwia zapisywanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowania znaków. Aby uzyskać informacji na temat zestawów znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.  
  
 Jeśli chcesz ustawić zestaw znaków źródła i wykonania zestawu znaków na UTF-8, możesz użyć **/UTF-8** — opcja kompilatora jako skrót. Jest równoznaczne z użyciem **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również włącza **/Validate-Charset** opcja domyślnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **/Execution-Charset** opcji, a następnie określ preferowany kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Source-Charset (Ustaw źródłowy zestaw znaków)](../../build/reference/source-charset-set-source-character-set.md)   
 [/ UTF-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)