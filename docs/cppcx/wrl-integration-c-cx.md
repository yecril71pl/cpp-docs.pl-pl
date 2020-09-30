---
title: Integracja z WRL (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: 3ea0f6aece985a2ee74916e737b9aab1bf0d1d96
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507414"
---
# <a name="wrl-integration-ccx"></a>Integracja z WRL (C++/CX)

Możesz swobodnie mieszać kod WRL za pomocą kodu biblioteki C++ (WRL) środowisko wykonawcze systemu Windows. W tej samej jednostce translacji można używać obiektów zadeklarowanych za pomocą notacji uchwytu WRL-to-Object ( `^` ) i WRL inteligentnego wskaźnika ( `ComPtr<T>` ). Należy jednak ręcznie obsłużyć wartości zwracane i WRL kody błędów HRESULT oraz wyjątki WRL.

## <a name="wrl-development"></a>Programowanie WRL

Aby uzyskać więcej informacji na temat tworzenia i używania składników WRL, zobacz [środowisko wykonawcze systemu Windows C++ Template Library (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Przykład

Poniższy fragment kodu ilustruje użycie WRL i WRL w celu użycia klas środowisko wykonawcze systemu Windows i przeanalizowania pliku metadanych.

Przykład jest pobierany ze fragmentu kodu na forum kompilowania aplikacji Microsoft Store. Autor tego fragmentu kodu oferuje następujące odrzuty i klauzule:

1. Język C++ nie zapewnia określonych interfejsów API do odzwierciedlenia na typach środowisko wykonawcze systemu Windows, ale pliki metadanych systemu Windows (WinMD) dla typu są w pełni zgodne z plikami metadanych CLR. System Windows udostępnia nowe interfejsy API odnajdowania metadanych (RoGetMetaDataFile), aby uzyskać dostęp do pliku winmd dla danego typu. Jednak te interfejsy API są ograniczone do deweloperów języka C++, ponieważ nie można utworzyć wystąpienia klasy.

1. Po skompilowaniu kodu należy również przekazać plik Runtimeobject. lib i Rometadata. lib do konsolidatora.

1. Ten fragment kodu jest prezentowany w postaci, w jakiej jest. Chociaż oczekiwanie działa prawidłowo, może ono zawierać błędy.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}
```

## <a name="see-also"></a>Zobacz też

[Współdziałanie z innymi językami](interoperating-with-other-languages-c-cx.md)
