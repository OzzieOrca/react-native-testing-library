// @flow
import { getByAPI } from './getByAPI';
import { queryByAPI } from './queryByAPI';
import a11yAPI from './a11yAPI';

const wrapFinder = (finder, instance) => (...args: any) =>
  finder.call(instance, ...args).map(wrapInstance);

const wrapInstance = (instance: ReactTestInstance): ReactTestInstance => {
  // $FlowFixMe
  Object.assign(instance, {
    findAll: wrapFinder(instance.findAll, instance),
    findAllByType: wrapFinder(instance.findAllByType, instance),
    findAllByProps: wrapFinder(instance.findAllByProps, instance),
    ...getByAPI(instance),
    ...queryByAPI(instance),
    ...a11yAPI(instance),
  });
  return instance;
};

export default wrapInstance;
