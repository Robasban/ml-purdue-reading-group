# 3D Guassian Splatting
Presenter: Alexandre Sauquet

## Summary
3D Guassian Splatting is a method to display 3D objects on a 2D surface. How it works is defining some object with 3D guassians, each having a color, opacity, and covariances and means. When the screen wants to display the object in 2D, it sends a ray off from each pixel out towards the object, and it uses a formula to add together the colors and opacities of all the guassians in that line until the opacity is 100%. At that point, the color for that pixel for the object is determined, and can be displayed. This process continues for every pixel on the screen until the object is displayed. This can be especially helpful in things like VR, where objects need to be displayed efficiently on screens.

## Notes
- No notes taken during meeting
