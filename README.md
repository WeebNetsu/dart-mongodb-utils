Couple of useful functions for when working with mongodb in Dart.

Example of usage

```dart
import 'package:groceries/utils/mongodb.dart';
import 'package:json_annotation/json_annotation.dart';
import 'package:whatever/this_package_items.dart';

part 'app_info.g.dart';

@JsonSerializable()
class AppInfoModel {
  /// Name of the collection in MongoDB
  static const collectionName = "appInfo";

  @JsonKey(
    name: '_id',
    fromJson: objectIdToString, // example of usage
    toJson: stringToObjectId,
  )
  final String? id;
  final int latestAppVersion;

  AppInfoModel({
    this.id,
    required this.latestAppVersion,
  });

  /// Constructs an [AppInfoModel] object from a JSON map.
  factory AppInfoModel.fromJson(Map<String, dynamic> json) => _$AppInfoModelFromJson(json);

  /// Constructs an JSON map object from [AppInfoModel].
  Map<String, dynamic> toJson() => _$AppInfoModelToJson(this);
}
```
