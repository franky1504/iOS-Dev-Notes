# 圖片縮放裁切

* extension UIImage

  ```
  func squareImage(image: UIImage) -> UIImage {
    return doResizeImage(doSquareImage(image), newSize: 100)
  }
  ```

  ​


* private extension UIImage
  ```
  func Min <T : Comparable> (a: T, b: T) -> T {
    if a > b {
        return b
    }
    return a
  }
  ```

* 將各種大小的圖裁切為正方形
  ```
  func doSquareImage(image: UIImage) -> UIImage {
    let originalWidth  = image.size.width * image.scale
    let originalHeight = image.size.height * image.scale
    print("\(originalWidth) X \(originalHeight)")

    let edge: CGFloat = Min(originalHeight, b: originalWidth)

    let posX = (originalWidth - edge) / 2.0
    let posY = (originalHeight - edge) / 2.0
    let cropSquare = CGRectMake(posX, posY, edge, edge)
    print("cropSquare: \(cropSquare)")

    UIGraphicsBeginImageContextWithOptions(cropSquare.size, false, image.scale);
    image.drawAtPoint(CGPointMake(-cropSquare.origin.x, -cropSquare.origin.y))
    let croppedImage = UIGraphicsGetImageFromCurrentImageContext();
    UIGraphicsEndImageContext();
    print("result Img:\(croppedImage.size)")

    return croppedImage
  }
  ```
* resize成100x100
  ```
  func doResizeImage(image: UIImage, newSize: CGFloat) -> UIImage {
    let oldsize = min(image.size.width, image.size.height)

    let scale = newSize / oldsize
    let newWidth = image.size.width * scale
    let newHeight = image.size.height * scale

    UIGraphicsBeginImageContext(CGSizeMake(newWidth, newHeight))
    image.drawInRect(CGRectMake(0, 0, newWidth, newHeight))
    let newImage = UIGraphicsGetImageFromCurrentImageContext()
    UIGraphicsEndImageContext()

    return newImage
  }
  ```