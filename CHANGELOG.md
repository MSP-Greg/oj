# CHANGELOG

## 2.18.5 - 2017-03-21 (2.18.4 was a bad release)
## 2.18.4 - 2017-03-21

- Thanks to ianks for adding the :empty_string option.

## 2.18.3 - 2017-03-14

- Changed to use long doubles for parsing to minimize round off errors. So PI will be accurate to more places for PI day.

## 2.18.2 - 2017-03-01

- Strict mode now allows symbol keys in hashes.

- Fixed omit_nil bug discovered by ysmazda.

## 2.18.1 - 2017-01-09

- Missing argument to dump now raises the correct arg exception and with mimic does not crash on missing argument.
- Oj::Doc paths can now contain escaped path separators so "a\/b" can match an lement name with a slash in it.

## 2.18.0 - 2016-11-26

- Rubinius compilation fixes.
- Added a separate option for as_json instead of piggy backing on the use_to_json. This changes the API slightly.
- Ready for Ruby 2.4.
- Thanks to faucct for fixing mimic to not redefine JSON::ParseError.

## 2.17.5 - 2016-10-19

- Added additional code to check for as_json arguments and recursive calls.

## 2.17.4 - 2016-09-04

- Added the ascii_only option to JSON.generate when in mimic_JSON mode so that it is consistent with the undocumented feature in the json gem.

## 2.17.3 - 2016-08-16

- Updated mimic_JSON to monkey patch OpenStruct, Range, Rational, Regexp, Struct, Symbol, and Time like the JSON gem does. Also added the JSON.create_id accessor.

## 2.17.2 - 2016-08-13

- Worked around a problem with DateTime and ActiveSupport that causes a hang when hour, minute, second, and some other methods are called from C.

## 2.17.1 - 2016-07-08

- Added an option provide an alternative Hash class for loading.
- Added the Oj::EasyHash class.
- Fixed test failures on 32 bit machines.
- Sped up mimic_JSON.
- Added an option to omit Hash and Object attributes with nil values.

## 2.16.1 - 2016-06-21

- Thanks to hsbt for fixing a compile issue with Ruby 2.4.0-preview1.

## 2.16.0 - 2016-06-19

- Added option to allow invalid unicode characters. This is not a suggested option in a majority of the cases.
- Fixed float parsing for 32 bit systems so that it does not roll over to BigDecimal until more than 15 significant digits.

## 2.15.1 - 2016-05-26

- Fixed bug with activerecord when to_json returns an array instead of a string.

## 2.15.0 - 2016-03-28

- Fixed bug where encoded strings could be GCed.
- :nan option added for dumping Infinity, -Infinity, and NaN. This is an edition to the API. The default value for the :non option is :auto which uses the previous NaN handling on dumping of non-object modes.

## 2.14.7 - 2016-03-20

- Fixed bug where a comment before another JSON element caused an error. Comments are not part of the spec but this keep support consistent.

## 2.14.6 - 2016-02-26

- Changed JSON::ParserError to inherit from JSON::JSONError which inherits from StandardError.

## 2.14.5 - 2016-02-19

- Parse errors in mimic mode are not a separate class than Oj.ParseError so the displayed name is JSON::ParserError instead.

## 2.14.4 - 2016-02-04

- When not in quirks mode strings are now raise an exception if they are the top level JSON value.

## 2.14.3 - 2015-12-31

- Updated to support Ruby 2.3.0.

## 2.14.2 - 2015-12-19

- Non-UTF-8 string input is now converted to UTF-8.

## 2.14.1 - 2015-12-15

- Fixed bug that reverted to BigDecimal when a decimal had preceeding zeros after the decimal point.

## 2.14.0 - 2015-12-04

- More tweaking on decimal rounding.
- Made dump options available in the default options and not only in the mimic generate calls.

## 2.13.1 - 2015-11-16

- Thanks to Comboy for the fix to a large number rounding bug.

## 2.13.0 - 2015-10-19

- Oj no longer raises an exception if the to_hash method of an object does not return a Hash. ActiveRecord has decided that to_hash should return an Array instead so Oj now encodes what ever is returned.
- Added a register_odd_raw function that allows odd marshal functions to return raw JSON as a string to be included in the dumped JSON.
- The register_odd function now supports modules in additions to classes.

## 2.12.14 - 2015-09-14

- Change the failure mode for objects that can not be serialized such as a socket. Now in compat mode the to_s of the object is placed in the output instead of raising an exception.

## 2.12.13 - 2015-09-02

- Added a check for the second argument to load() is a Hash.
- Yet another attempt to make floating point numbers display better.
- Thanks to mkillianey for getting the extconf.rb and gemspec file updated.

## 2.12.12 - 2015-08-09

- Thanks to asurin for adding support for arguments to to_json() that rails uses.

## 2.12.11 - 2015-08-02

- Oj::ParseError is now thrown instead of SyntaxError when there are multiple  JSON documents in a string or file and there is no proc or block associated with the parse call.

## 2.12.10 - 2015-07-12

- An exception is now raised if there are multiple JSON documents in a string or file if there is no proc or block associated with the parse call.

## 2.12.9 - 2015-05-30

- Fixed failing test when using Rubinius.
- Changed mimic_JSON to support the global/kernel function JSON even when the json gem is loaded first.

## 2.12.8 - 2015-05-16

- mimic_JSON now supports the global/kernel JSON function that will either parse a string argument or dump an array or object argument.

## 2.12.7 - 2015-05-07

- Fixed compile error with 32 bit HAS_NANO_TIME extra paren bug.

## 2.12.6 - 2015-05-05

- Fixed a number of 32bit related bugs.

## 2.12.5 - 2015-04-27

- In :null mode Oj now dumps Infinity and NaN as null.

## 2.12.4 - 2015-04-20

- Fixed memory leak in Oj::Doc when not using a given proc.

## 2.12.3 - 2015-04-16

- Fixed bug when trying to resolve an invalid class path in object mode load.

## 2.12.2 - 2015-04-13

- Fixed Oj::Doc bug that causes a crash on local name lookups.
- Fixed Oj::Doc unicode parsing.

## 2.12.1 - 2015-03-12

- Changed the unix_zone encoded format to be the utc epoch.

## 2.12.0 - 2015-03-06

- String formats for UTC time are now explitly UTC instead of offset of zero. This fixes a problem with pre-2.2.0 Rubies that automatically convert zero offset times to local times.
- Added :unix_zone time_format option for formating numeric time. This option is the same as the :unix time option but the UTC offset is included as an exponent to the number time value. A value of 86400 is an indication of UTC time.

## 2.11.5 - 2015-02-25

- Fixed issue with rails as_json not being called for Structs.
- Added support for anonymous Structs with object mode encoding. Note that this will result in a new anonymous Struct for each instance.

## 2.11.4 - 2015-01-20

- DateTime second encoding is now always a Rational to preserve accuracy.
- Fixed buf in the Oj.load() callback feature that caused an endless loop when a StringIO was used with a JSON that was a number.

## 2.11.3 - 2015-01-18

- DateTime encoding now includes nanoseconds.

## 2.11.2 - 2015-01-10

- Changed the defaults for mimic_JSON to use 16 significant digits instead of the default 15.
- Fixed bug where a subclass of Array would be serialized as if in object mode instead of compat when in compat mode.

## 2.11.1 - 2014-11-09

- Changed the use_to_json option to still allow as_json even when set to false.

## 2.11.0 - 2014-11-02

- Restricted strict dump to not dump NaN nor Infinity but instead raise an exception.
- Changed compat mode so that the :bigdecimal_as_decimal option over-rides the to_json method if the option is true. The default for mimic_JSON is to leave the option off.
- Added support for Module encoding in compat mode.
- Added ActiveSupportHelper so that require 'active_support_helper' will added a helper for serializing ActiveSupport::TimeWithZone.
- Added float_precision option to control the number of digits used for floats when dumping.

## 2.10.4 - 2014-10-22

- Fixed Range encoding in compat mode to not use the object mode encoding.
- Fixed serialization problem with timestamps.
- Fixed compat parser to accept NaN and Infinity.

## 2.10.3 - 2014-10-04

- Using the xmlschema option with :object mode now saves time as a string and preserves the timezone.
- Rational recursive loop caused by active support fixed.
- Time in mimic_JSON mode are now the ruby string representation of a date.

## 2.10.2 - 2014-08-20

- Fixed string corruption bug due to an uncommented assignment used for debugging.

## 2.10.1 - 2014-08-17

- Changed parse argument error to be a Ruby ArgError instead of a general Exception.

## 2.10.0 - 2014-08-03

- Using an indent of less than zero will not place newline characters between JSON elements when using the string or stream writer.
- A new options callback method was added to the Simple Callback Parser. If defined the prepare_key() method will be called when an JSON object ket is first encountered. The return value is then used as the key in the key-value pair.
- Increased significants digits to 16 from 15. On occasion there may be unexpected round off results. Tou avoid those use the bigdecimal options.

## 2.9.9 - 2014-07-07

- Missed a character map entry. / in ascii mode is now output as / and not \/
- Fixed SC parser to not treat all IO that respond to fileno as a file. It not checks stat and asks if it is a file.
- Tightened object parsing of non-string hash keys so that just "^#x" is parsed as a hash pair and not "~#x".
- Using echo to STDIN as an IO input works around the exception raised when asking the IO for it's position (IO.pos).
- Simple Callback Parser now uses the new stream parser for handling files and IO so that larger files are handled more efficiently and streams are read as data arrives instead of on close.
- Handles file FIFO pipes correctly now.

## 2.9.8 - 2014-06-25

- Changed escaping back to previous release and added a new escape mode.
- Strict mode and compat mode no longer parse Infinity or NaN as a valid number. Both are valid in object mode still.

## 2.9.7 - 2014-06-24

- Changed dump to use raw / and raw \n in output instead of escaping.
- Changed the writer to always put a new line at the end of a top level JSON object. It makes output easier to view and edit with minimal impact on size.
- Worked around the file.gets look ahead caching as long as it is not called while parsing (of course).
- Thanks to lautis for a new parse option. quirks_mode allows Oj to behave quirky like the JSON gem. Actually the JSON gem has it backwards with quirky mode supporting the JSON spec and non-quirky limiting parsing to objects and arrays. Oj stays consistent with the JSON gem to avoid confusion.
- Fixed problem with sc_parse not terminating the string when loaded from a file.
- Thanks go to dchelimsky for expanding the code sample for the ScHandler.

## 2.9.6 - 2014-06-15

- Fixed bug using StringIO with SCParser.
- Tightened up JSON mimic to raise an exception if JSON.parse is called on a JSON documents that returns a primitive type.

## 2.9.5 - 2014-06-07

- Mimic mode now monkey patches Object like JSON.
- A big thanks to krasnoukhov for reorganizing test and helping get Oj more rails compatible.
- Another thanks goes out to lautis for a pull request that provided some optimization and fixed the return exception for an embedded null in a string.
- Fixed a bug with zip reader streams where EOF was not handled nicely.

## 2.9.4 - 2014-05-28

- In mimic mode parse errors now match the JSON::ParserError.

## 2.9.3 - 2014-05-15

- Fixed IO read error that showed up in IO objects that return nil instead of raising an EOF error when read is done.

## 2.9.2 - 2014-05-14

- Fixed link error with Windows.

## 2.9.1 - 2014-05-14

- Fixed mimic load when given a block to evalate. It conflicted with the new load option.
- Added a true stream that is used when the input argument to load is an IO object such as a stream or file. This is slightly slower for smaller files but allows reading of huge files that will not fit in memory and is more efficient on even larger files that would fit into memory. The load_file() method uses the new stream parser so multiple GB files can be processed without used execessive memory.

## 2.9.0 - 2014-05-01

- Added support for detection and handling of Strng, Array, and Hash subclasses.
- Oj.load() can now take a block which will be yielded to on every object parsed when used with a file or string with multiple JSON entries.

## 2.8.1 - 2014-04-21

- Added additional argument to the register_odd function.
- Fixed bug that failed to load on some uses of STDIN.

## 2.8.0 - 2014-04-20

- Added support for registering special encoding and decoding rules for specific classes. This the ActiveSupport subclass of the String class for safe strings. For an example look at the `test_object.rb` file, `test_odd_string` test.

## 2.7.3 - 2014-04-11

- Fixed bug where load and dump of Structs in modules did not work correctly.

## 2.7.2 - 2014-04-06

- Added option return nil if nil is provided as input to load.

## 2.7.1 - 2014-03-30

- Fixed bug in new push_key which caused duplicate characters.

## 2.7.0 - 2014-03-29

- Added the push_key() method to the StringWriter and StreamWriter classes.

## 2.6.1 - 2014-03-21

- Set a limit on the maximum nesting depth to 1000. An exception is raised instead of a segfault unless a reduced stack is used which could trigger the segfault due to an out of memory condition.

## 2.6.0 - 2014-03-11

- Added the :use_to_json option for Oj.dump(). If this option is set to false the to_json() method on objects will not be called when dumping. This is the default behavior. The reason behind the option and change is to better support Rails and ActiveSupport. Previous works arounds have been removed.

## 2.5.5 - 2014-02-18

- Worked around the Rubinius failure to load bigdecimal from a require within the C code.

## 2.5.4 - 2014-01-14

- Fixed bug where unterminated JSON did not raise an exception.

## 2.5.3 - 2014-01-03

- Added support for blocks with StringWriter.

## 2.5.2 - 2014-01-02

- Fixed indent problem with StringWriter so it now indents properly.

## 2.5.1 - 2013-12-18

- Added push_json() to the StringWriter and StreamWriter to allow raw JSON to be added to a JSON document being constructed.

## 2.4.3 - 2013-12-16

- Made include pthread.h conditional for Windows.

## 2.4.2 - 2013-12-14

- Thanks to Patrik Rak for a fix to a buffer short copy when dumping with 0 indent.

## 2.4.1 - 2013-12-10

- Fixed Windows version by removing class cache test.

## 2.4.0 - 2013-12-08

- Merged in a PR to again allow strings with embedded nulls.
- Implemented StreamWriter to compliment the StringWriter.
- Fixed bug in the class cache hash function that showed up with the sparc compiler.

## 2.3.0 - 2013-12-01

- JRuby is no longer supported.
- Thanks to Stefan Kaes the support for structs has been optimized.
- Better support for Rubinous.
- Added option to disable GG during parsing.
- Added StringWriter that allows building a JSON document one element at a time.

## 2.2.3 - 2013-11-19

- Fixed struct segfault on load.
- Added option to force float on load if a decimal number.

## 2.2.2 - 2013-11-17

- Added mutex support for Windows.
- Protected SCP parser for GC.

## 2.2.1 - 2013-11-15

- Made all VALUEs in parse volatile to avoid garbage collection while in use.

## 2.2.0 - 2013-11-11

- All 1.8.x versions of Ruby now have require 'rational' called.
- Removed the temporary GC disable and implemented mark strategy instead.
- Added new character encoding mode to support the Rails 4 escape characters of &,  as xss_safe mode. The :encoding option replaces the :ascii_only option.
- Change parsing of NaN to not use math.h which on older systems does not define NAN.

## 2.1.8 - 2013-10-28

- All 1.8.x versions of Ruby now have require 'rational' called.
- Removed the temporary GC disable and implemented mark strategy instead.

## 2.1.7 - 2013-10-19

- Added support for NaN and -NaN to address issue #102. This is not according to the JSON spec but seems to be expected.
- Added require for rational if the Ruby version is 1.8.7 to address issue #104.
- Added Rails re-call of Oj.dump in the to_json() method which caused loops with Rational objects to fix issue #108 and #105.

## 2.1.6 - 2013-10-07

- Added Oj.to_stream() for dumping JSON to an IO object.

## 2.1.5 - 2013-07-21

- Allow exception dumping magic with Windows.

## 2.1.4 - 2013-07-04

- Fixed Linux 32 bit rounding bug.

## 2.1.3 - 2013-06-30

- Fixed bug that did not deserialize all attributes in an Exception subclass.
- Added a sample to demonstrate how to write Exception subclasses that will automatically serialize and deserialize.

## 2.1.2 - 2013-06-19

- Fixed support for Windows.

## 2.1.1 - 2013-06-17

- Fixed off by 1 error in buffer for escaped strings.

## 2.1.0 - 2013-06-16

- This version is a major rewrite of the parser. The parser now uses a constant stack size no matter how deeply nested the JSON document is. The parser is also slightly faster for larger documents and 30% faster for object parsing.
- Oj.strict_load() was renamed to Oj.safe_load() to better represent its functionality. A new Oj.strict_load() is simply Oj.load() with :mode set to :strict.
- Oj.compat_load() and Oj.object_load() added.
- A new Simple Callback Parser was added invoked by Oj.sc_parse().
- Eliminated :max_stack option as it is no longer needed.
- Handle cleanup after exceptions better.

## 2.0.14 - 2013-05-26

- Fixed bug in Oj::Doc.each_leaf that caused an incorrect where path to be created and also added a check for where path maximum length.
- Updated the documentation to note that invalid JSON documents, which includes an empty string or file, will cause an exception to be raised.

## 2.0.13 - 2013-05-17

- Changed dump to put closing array brackets and closing object curlies on the line following the last element if :indent is set to greater than zero.

## 2.0.12 - 2013-04-28

- Another fix for mimic.
- mimic_JSON now can now be called after loading the json gem. This will replace the json gem methods after loading. This may be more compatible in many cases.

## 2.0.11 - 2013-04-23

- Fixed mimic issue with Debian
- Added option to not cache classes when loading. This should be used when classes are dynamically unloaded and the redefined.
- Float rounding improved by limiting decimal places to 15 places.
- Fixed xml time dumping test.

## 2.0.10 - 2013-03-10

- Tweaked dump calls by reducing preallocation. Speeds are now several times faster for smaller objects.
- Fixed Windows compile error with Ruby 2.0.0.

## 2.0.9 - 2013-03-04

- Fixed problem with INFINITY with CentOS and Ruby 2.0.0. There are some header file conflicts so a different INFINITY was used.

## 2.0.8 - 2013-03-01

- Added :bigdecimal_load option that forces all decimals in a JSON string to be read as BigDecimals instead of as Floats. This is useful if precision is important.
- Worked around bug in active_support 2.3.x where BigDecimal.as_json() returned self instead of a JSON primitive. Of course that creates a loop and blows the stack. Oj ignores the as_json() for any object that returns itself and instead encodes the object as it sees fit which is usually what is expected.
- All tests pass with Ruby 2.0.0-p0. Had to modify Exception encoding slightly.

## 2.0.7 - 2013-02-18

- Fixed bug where undefined classes specified in a JSON document would freeze Ruby instead of raising an exception when the auto_define option was not set. (It seems that Ruby freezes on trying to add variables to nil.)

## 2.0.6 - 2013-02-18

- Worked around an undocumented feature in linux when using make that misreports the stack limits.

## 2.0.5 - 2013-02-16

- DateTimes are now output the same in compat mode for both 1.8.7 and 1.9.3 even though they are implemented differently in each Ruby.
- Objects implemented as data structs can now change the encoding by implemented either to_json(), as_json(), or to_hash().
- Added an option to allow BigDecimals to be dumped as either a string or as a number. There was no agreement on which was the best or correct so both are possible with the correct option setting.

## 2.0.4 - 2013-02-11

- Fixed bug related to long class names.
- Change the default for the auto_define option.
- Added Oj.strict_load() method that sets the options to public safe options. This should be safe for loading JSON documents from a public unverified source. It does not eleviate to need for reasonable programming practices of course. See the section on the proper use of Oj in a public exposure.

## 2.0.3 - 2013-02-03

- Fixed round off error in time format when rounding up to the next second.

## 2.0.2 - 2013-01-23

- Fixed bug in Oj.load where loading a hash with symbold keys and also turning on symbolize keys would try to symbolize a symbol.

## 2.0.1 - 2013-01-15

- BigDecimals now dump to a string in compat mode thanks to cgriego.
- High precision time (nano time) can be turned off for better compatibility with other JSON parsers.
- Times before 1970 now encode correctly.

## 2.0.0 - 2012-12-18

- Thanks to yuki24 Floats are now output with a decimal even if they are an integer value.
- The Simple API for JSON (SAJ) API has been added. Read more about it on the Oj::Saj page.

## 1.4.7 - 2012-12-09

- In compat mode non-String keys are converted to Strings instead of raising and error. (issue #52)

## 1.4.6 - 2012-12-03

- Silently ignores BOM on files and Strings.
- Now works with JRuby 1.7.0 to the extent possible with the unsupported C extension in JRuby.

## 1.4.5 - 2012-11-19

- Adds the old deprecated methods of unparse(), fast_unparse(), and pretty_unparse() to JSON_mimic.

## 1.4.4 - 2012-11-07

- Fixed bug in mimic that missed mimicing json_pure.

## 1.4.3 - 2012-10-19

- Fixed Exception encoding in Windows version.

## 1.4.2 - 2012-10-17

- Fixed dump and load of BigDecimals in :object mode.
- BigDecimals are now dumped and loaded in all modes.

## 1.4.1 - 2012-10-17

- Windows RubyInstaller and TCS-Ruby now supported thanks to Jarmo Pertman. Thanks Jarmo.

## 1.4.0 - 2012-10-11

- Parse errors now raise an Exception that inherites form Oj::Error which inherits from StandardError. Some other Exceptions were changed as well to make it easier to rescue errors.

## 1.3.7 - 2012-10-05

- Added header file for linux builds.

## 1.3.6 - 2012-10-04

- Oj.load() now raises a SystemStackError if a JSON is too deeply nested. The loading is allowed to use on 75% of the stack.
- Oj::Doc.open() now raises a SystemStackError if a JSON is too deeply nested. The loading is allowed to use on 75% of the stack. Oj::Doc.open will allow much deeper nesting than Oj.load().

## 1.3.5 - 2012-09-25

- Fixed mimic_JSON so it convinces Ruby that the ALL versions of the json gem are already loaded.

## 1.3.4 - 2012-08-12

- Fixed mimic_JSON so it convinces Ruby that the json gem is already loaded.

## 1.3.2 - 2012-07-28

- Fixed compile problems with native Ruby on OS X 10.8 (Mountain Lion)

## 1.3.1 - 2012-07-01

- Fixed time zone issue with :xmlschema date format.

## 1.3.0 - 2012-07-09

- extconf.rb fixed to not pause on some OSs when checking CentOS special case.
- Added an option to control the time format output when in :compat mode.

## 1.2.13 - 2012-07-08

- Fixed double free bug in Oj::Doc that showed up for larger documents.

## 1.2.12 - 2012-07-06

- Fixed GC bug in Oj::Doc, the fast parser.
- Serialization of Exceptions in Ruby 1.8.7 now includes message and backtrace.

## 1.2.11 - 2012-06-21

- Added :max_stack option to limit the size of string allocated on the stack.

## 1.2.10 - 2012-06-20

- Added check for circular on loading of circular dumped JSON.
- Added support for direct serialization of BigDecimal, Rational, Date, and DateTime.
- Added json.rb to $" in mimic mode to avoid pulling in the real JSON by accident.
- Oj is now thread safe for all functions.
- The / (solidus) character is now placed in strings without being escaped.

## 1.2.9 - 2012-05-29


## 1.2.8 - 2012-05-03

- Included a contribution by nevans to fix a math.h issue with an old fedora linux machine.
- Included a fix to the documentation found by mat.

## 1.2.7 - 2012-04-22

- Fixed bug where a float with too many characters would generate an error. It is not parsed as accuractly as Ruby will support.
- Cleaned up documentation errors.
- Added support for OS X Ruby 1.8.7.

## 1.2.6 - 2012-04-22

- Cleaned up documentation errors.
- Added support for OS X Ruby 1.8.7.

## 1.2.5 - 2012-04-18

- Added support for create_id in Oj and in mimic_JSON mode

## 1.2.4 - 2012-04-13

- Removed all use of math.h to get around CentOS 5.4 compile problem.

## 1.2.3 - 2012-04-09

- Fixed compile error for the latest RBX on Travis.

## 1.2.2 - 2012-04-02

- minor bug fixes for different rubies along with test updates
- Oj::Doc will now automatically close on GC.

## 1.2.1 - 2012-03-30

- Organized compile configuration better.
- as_json() support now more flexible thanks to a contribution by sauliusg.

## 1.2.0 - 2012-03-30

- Removed the encoding option and fixed a misunderstanding of the string encoding. Unicode code points are now used instead of byte codes. This is not compatible with previous releases but is compliant with RFC4627.
- Time encoding in :object mode is faster and higher nanosecond precision.

## 1.1.1 - 2012-03-27

- The encoding option can now be an Encoding Object or a String.
- Fixed Rubinius errors.

## 1.1.0 - 2012-03-27

- Errors are not longer raised when comments are encountered in JSON documents.
- Oj can now mimic JSON. With some expections calling JSON.mimic_JSON will allow all JSON calls to use OJ instead of JSON. This gives a speedup of more than 2x on parsing and 5x for generating over the JSON::Ext module.
- Oj::Doc now allows a document to be left open and then closed with the Oj::Doc.close() class.
- Changed the default encoding to UTF-8 instead of the Ruby default String encoding.

## 1.0.6 - 2012-03-20

- Gave Oj::Doc a speed increase. It is now 8 times fast than JSON::Ext.

## 1.0.5 - 2012-03-17

- Added :ascii_only options for dumping JSON where all high-bit characters are encoded as escaped sequences.

## 1.0.4 - 2012-03-16

- Fixed bug that did not allow symbols as keys in :compat mode.

## 1.0.3 - 2012-03-15

- Added :symbol_keys option to convert String hash keys into Symbols.
- The load() method now supports IO Objects as input as well as Strings.

## 1.0.2 - 2012-03-15

- Added RSTRING_NOT_MODIFIED for Rubinius optimization.

## 1.0.1 - 2012-03-15

- Fixed compatibility problems with Ruby 1.8.7.

## 1.0.0 - 2012-03-13

- The screaming fast Oj::Doc parser added.

## 0.9.0 - 2012-03-05

- Added support for circular references.

## 0.8.0 - 2012-02-27

- Auto creation of data classes when unmarshalling Objects if the Class is not defined

## 0.7.0 - 2012-02-26

- changed the object JSON format
- serialized Ruby Objects can now be deserialized
- improved performance testing

## 0.6.0 - 2012-02-22

- supports arbitrary Object dumping/serialization
- to_hash() method called if the Object responds to to_hash and the result is converted to JSON
- to_json() method called if the Object responds to to_json
- almost any Object can be dumped, including Exceptions (not including Thread, Mutex and Objects that only make sense within a process)
- default options have been added

## 0.5.2 - 2012-02-19

- Release 0.5.2 fixes encoding and float encoding.
- This is the first release sith a version of 0.5 indicating it is only half done. Basic load() and dump() is supported for Hash, Array, NilClass, TrueClass, FalseClass, Fixnum, Float, Symbol, and String Objects.

## 0.5.1 - 2012-02-19


## 0.5 - 2012-02-19

- This is the first release with a version of 0.5 indicating it is only half done. Basic load() and dump() is supported for Hash, Array, NilClass, TrueClass, FalseClass, Fixnum, Float, Symbol, and String Objects.
