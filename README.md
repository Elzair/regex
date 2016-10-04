# boost.regex

Regular expressions are a form of pattern-matching that are often used in text processing; many users will be familiar with the Unix utilities grep, sed and awk, and the programming language Perl, each of which make extensive use of regular expressions. Traditionally C++ users have been limited to the POSIX C API's for manipulating regular expressions, and while Boost.Regex does provide these API's, they do not represent the best way to use the library. For example Boost.Regex can cope with wide character strings, or search and replace operations (in a manner analogous to either sed or Perl), something that traditional C libraries can not do.

## Boost Dependencies

[Boost.Assert](https://github.com/boostorg/assert)
[Boost.ConceptCheck](https://github.com/boostorg/concept_check)
[Boost.Config](https://github.com/boostorg/config)
[Boost.Conversion](https://github.com/boostorg/conversion)
[Boost.Core](https://github.com/boostorg/core)
[Boost.Detail](https://github.com/boostorg/detail)
[Boost.Function](https://github.com/boostorg/function)
[Boost.FunctionTypes](https://github.com/boostorg/function_types)
[Boost.Functional](https://github.com/boostorg/functional)
[Boost.Fusion](https://github.com/boostorg/fusion)
[Boost.Integer](https://github.com/boostorg/integer)
[Boost.Iterator](https://github.com/boostorg/iterator)
[Boost.MPL](https://github.com/boostorg/mpl)
[Boost.Optional](https://github.com/boostorg/optional)
[Boost.Predef](https://github.com/boostorg/predef)
[Boost.Preprocessor](https://github.com/boostorg/preprocessor)
[Boost.Range](https://github.com/boostorg/range)
[Boost.SmartPtr](https://github.com/boostorg/smart_ptr)
[Boost.StaticAssert](https://github.com/boostorg/static_assert)
[Boost.ThrowException](https://github.com/boostorg/throw_exception)
[Boost.Tuple](https://github.com/boostorg/tuple)
[Boost.TypeIndex](https://github.com/boostorg/type_index)
[Boost.TypeTraits](https://github.com/boostorg/type_traits)
[Boost.Typeof](https://github.com/boostorg/typeof)
[Boost.Utility](https://github.com/boostorg/utility)


## More information

* [Documentation](http://boost.org/libs/regex)
* [Report bugs](https://svn.boost.org/trac/boost/newticket?component=regex;version=Boost%20Release%20Branch). Be sure to mention Boost version, platform and compiler you're using. A small compilable code sample to reproduce the problem is always good as well.
* Submit your patches as pull requests against **develop** branch. Note that by submitting patches you agree to license your modifications under the [Boost Software License, Version 1.0](http://www.boost.org/LICENSE_1_0.txt).

## License

Distributed under the [Boost Software License, Version 1.0](http://www.boost.org/LICENSE_1_0.txt).
