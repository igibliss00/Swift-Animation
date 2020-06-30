# Swift Animation

An iPadOS app that demonstrates the use case of the UIView animation methods as well as the CGAffineTransform method.  Project 15 of HackingWithSwift.com

<img src="https://github.com/igibliss00/Swift-Animation/blob/master/README_assets/1.png" width="400">
<img src="https://github.com/igibliss00/Swift-Animation/blob/master/README_assets/2.png" width="400">

## Features

### animate(withDuration:delay:options:animations:completion: )

This is one of the UIView animation methods.  The beauty is that you don’t need to configure anything frame by frame and you only need to provide the 5 parameters. 

- withDuration: This is to indicate how long the animation should last.
- delay: This is the time frame after which the animation should start.
- options: This is how you want to perform the animation. Following are some of the options, but not all.
    - allowUserInteraction
    - layoutSubview
    - repeat
    - beginFromCurrentState
    - autoreverse
    - overrideInheritedCurve
    - overrideInheritedDuration
    - allowAnimatedContent
    - showHideTransitionViews
    - curveEaseInOut: this is by default
    - curveEaseIn
    - curveEaseOut
    - curveLinear
    - transitionFlipFromLeft
- animations: This is where you programmatically specify which view and animatable properties to animate.  This parameter cannot be null.  As mentioned before, you don’t need to give a frame-by-frame instructions, but only the final value and Swift will do the rest.
- completion: This is where you input what happens either when the animation is naturally finished or interrupted.  Takes a single Boolean value, which is to indicate whether the former or the latter.  Unlike the animations parameter, this parameter may be null.  

```
 UIView.animate(withDuration: 1, delay: 0, usingSpringWithDamping: 0.5, initialSpringVelocity: 5, options: [], animations: {
            switch self.currentAnimation {
            case 0:
                self.imageView.transform = CGAffineTransform(scaleX: 2, y: 2)
                break
            case 1:
                self.imageView.transform = .identity
            case 2:
                self.imageView.transform = CGAffineTransform(translationX: -256, y: -256)
            case 3:
                self.imageView.transform = .identity
            case 4:
                self.imageView.transform = CGAffineTransform(rotationAngle: .pi)
            case 5:
                self.imageView.transform = .identity
            case 6:
                self.imageView.alpha = 0.1
                self.imageView.backgroundColor = .green
            case 7:
                self.imageView.alpha = 1
                self.imageView.backgroundColor = .clear
            default:
                break
            }
        }) { (finished ) in
            sender.isHidden = false
        }
        
        currentAnimation += 1
        
        if currentAnimation > 7 {
            currentAnimation = 0
        }
```

### CGAffineTransform

An affine transformation matrix is used to rotate, scale, translate, or skew the objects you draw in a graphics context. The CGAffineTransform type provides functions for creating, concatenating, and applying affine transformations. ([Source](https://developer.apple.com/documentation/coregraphics/cgaffinetransform))
