---
title: /STD (Określ wersję standardową języka)
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 52aa99cf5bdf7ddcf83a8423b946a03d2ca95d2d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079265"
---
# <a name="std-specify-language-standard-version"></a>/STD (Określ wersję standardową języka)

Włącz obsługiwane C++ funkcje językowe z określonej wersji standardu C++ językowego.

## <a name="syntax"></a>Składnia

> /std:\[c++ 14\|c++ 17\|c + + Najnowsza]

## <a name="remarks"></a>Uwagi

Opcja **/STD** jest dostępna w programie Visual Studio 2017 i nowszych. Służy do kontrolowania funkcji standardowego języka programowania ISO C++ , które są włączone podczas kompilowania kodu. Ta opcja umożliwia wyłączenie obsługi niektórych nowych funkcji języka i biblioteki, które mogą spowodować uszkodzenie istniejącego kodu, który jest zgodny z określoną wersją standardu języka. Domyślnie **/std: c++ 14** jest określony, co powoduje wyłączenie funkcji języka i standardowej biblioteki, które znajdują się w nowszych C++ wersjach standardu języka. Użyj **/std: c++ 17** , aby włączyć funkcje i zachowanie specyficzne dla języka c++ 17. Aby jawnie włączyć aktualnie zaimplementowane funkcje kompilatora i biblioteki standardowej proponowane dla następnej wersji Standard, użyj **/std: c + + Najnowsza**. Wszystkie funkcje języka C++ 20 wymagają **/std: C + + Najnowsza**; Po zakończeniu implementacji zostanie włączona Nowa opcja **/std: c++ 20** .

Domyślna opcja **/std: c++ 14** włącza zestaw funkcji języka c++ 14 wdrożonych przez kompilator MSVC. Ta opcja powoduje wyłączenie obsługi biblioteki kompilatora i standardowej dla funkcji, które są zmieniane lub nowe w nowszych wersjach Standard języka, z wyjątkiem niektórych funkcji C++ 17 już zaimplementowanych w poprzednich wersjach kompilatora MSVC. Aby uniknąć istotnej zmiany dla użytkowników, którzy już korzystali z funkcji dostępnych w programie Visual Studio 2015 Update 2, te funkcje pozostają włączone, gdy zostanie określona opcja **/std: c++ 14** :

- [Reguły dla Autotekstu z klamrami-init-list](https://wg21.link/n3922)

- [TypeName w szablonie szablonu — parametry](https://wg21.link/n4051)

- [Usuwanie trigraphs](https://wg21.link/n4086)

- [Atrybuty dla przestrzeni nazw i modułów wyliczających](https://wg21.link/n4266)

- [literały znaków U8](https://wg21.link/n4267)

Aby uzyskać dodatkowe informacje o tym, które funkcje języka C++ 14 i C++ 17 są włączone, gdy **/std: c++ 14** jest określony, zobacz uwagi w [tabeli zgodność z językiem Microsoft C++ ](../../overview/visual-cpp-language-conformance.md).

Opcja **/std: c++ 17** umożliwia korzystanie z pełnego zestawu funkcji języka c++ 17 wdrożonych przez kompilator MSVC. Ta opcja powoduje wyłączenie obsługi biblioteki kompilatora i standardowej dla funkcji, które są zmieniane lub nowe w wersjach roboczych roboczej i aktualizacji wad C++ standard po c++ 17.

Opcja **/std: c + + Najnowsza** włącza funkcje języka post-c + + 17, które są obecnie zaimplementowane w kompilatorze i bibliotekach. Mogą one obejmować funkcje z roboczej wersji języka C++ 20 i aktualizacje usterek C++ standardowego, które nie są uwzględnione w języku c++ 17, a także eksperymentalne propozycje dotyczące wersji Standard. Aby zapoznać się z listą obsługiwanych języków i funkcji biblioteki, zobacz [co nowego w C++programie Visual ](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). Opcja **/std: c + + Najnowsza** nie włącza funkcji chronionych przez przełącznik **/Experimental** , ale może być wymagana, aby je włączyć.

> [!IMPORTANT]
> Funkcje kompilatora i biblioteki włączane przez **/std: c + + Najnowsza** reprezentuje funkcje, które mogą być wyświetlane w C++ przyszłości, a także funkcje języka c++ 20, które są zatwierdzone. Funkcje, które nie zostały zatwierdzone, podlegają istotnym zmianom lub usunięciu bez powiadomienia i są udostępniane na bieżąco.

Opcja **/STD** w działaniu podczas C++ kompilacji może zostać wykryta przy użyciu makra preprocesora [\_MSVC\_lang](../../preprocessor/predefined-macros.md) . Aby uzyskać więcej informacji, zobacz [makra preprocesora](../../preprocessor/predefined-macros.md).

**/Std: c++ 14** i **/std: c + + najnowsze** opcje są dostępne, zaczynając od programu Visual Studio 2015 Update 3. Opcja **/std: c++ 17** jest dostępna począwszy od programu Visual Studio 2017 w wersji 15,3. Jak wspomniano powyżej, niektóre standardowe zachowanie języka C++ 17 jest włączane przez opcję **/std: c++ 14** , ale wszystkie inne funkcje c++ 17 są włączane przez **/std: c++ 17**. Funkcje języka c++ 20 są włączane przez **/std: Najnowsze** do momentu ukończenia implementacji.

> [!NOTE]
> W zależności od wersji kompilatora MSVC lub poziomu aktualizacji funkcje języka C++ 17 mogą nie być w pełni zaimplementowane lub w pełni zgodne po określeniu opcji **/std: c++ 17** . Aby zapoznać się z C++ omówieniem zgodności języka w Visual C++ w wersji wydanej, zobacz [tabela zgodność z językiem Microsoft C++ ](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **Język** **CC++/** .

1. W obszarze  **C++ Standard języka**wybierz Standard języka, który ma być obsługiwany przez kontrolkę listy rozwijanej, a następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
