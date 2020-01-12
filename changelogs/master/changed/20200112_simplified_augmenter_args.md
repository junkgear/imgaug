# Simplified Standard Parameters of Augmenters #567

Changed the standard parameters shared by all augmenters to a
reduced and more self-explaining set. Previously, all augmenters
shared the parameters `name`, `random_state` and `deterministic`.
The new parameters are `seed` and `name`.

`deterministic` was removed as it was hardly ever used and because
it caused frequently confusion with regards to its meaning. The
parameter is still accepted but will now produce a deprecation
warning. Use `<augmenter>.to_deterministic()` instead.

`random_state` was renamed to `seed` as providing a seed value
is the more common use case compared to providing a random state.
Many users also seemed to be unaware that `random_state` accepted
seed values. The new name should make this more clear.
The old parameter `random_state` is still accepted, but will
likely be deprecated in the future.

**[breaking]** This patch breaks if one relied on the order of
`name` and `random_state` instead of their names. These parameters
are now in inverted order, i.e. `(..., seed=None, name=None, ...)`
as seeds are much more commonly used than names. 
